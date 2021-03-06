# asus-fan-control

[![CI status](https://github.com/dominiksalvet/asus-fan-control/workflows/CI/badge.svg)](https://github.com/dominiksalvet/asus-fan-control/commits)
[![GitPack](https://img.shields.io/badge/-GitPack-571997)](https://github.com/dominiksalvet/gitpack)
[![standard-readme compliant](https://img.shields.io/badge/readme_style-standard-brightgreen.svg)](https://github.com/RichardLitt/standard-readme)

> Fan control for ASUS devices running Linux.

In default, some ASUS laptops running Linux control their system fans inappropriately. **Typical symptoms** include:

* Running fans even when not under any load
* Not running fans under load appropriately
* Spinning up fans in short performance peaks

This program solves the problems above and even more. It is also very easy to understand as it communicates with hardware exclusively using ACPI calls. **Tested ASUS models** with links to their first testers:

| ASUSPRO      | ROG                | VivoBook       | ZenBook            |
|--------------|--------------------|----------------|--------------------|
| [B9440UA][1] | [G752VL][2]        | [15 X510UA][4] | [Flip UX360UAK][6] |
|              | [Strix GL553VD][3] | [15 X512FA][5] | [UX410UA][7]       |
|              |                    |                | [UX430UA][8]       |

[1]: https://github.com/fzwoch
[2]: https://github.com/icegood
[3]: https://gitlab.com/infinito84
[4]: https://github.com/agura-lex
[5]: https://github.com/MartinMyr
[6]: https://github.com/afilipovich
[7]: https://github.com/fsanzdev
[8]: https://github.com/dominiksalvet

> Your laptop is not in the table yet? Take a look at [*CONTRIBUTING.md*](CONTRIBUTING.md) file and you can add it yourself.

## Table of Contents

* [Install](#install)
  * [Dependencies](#dependencies)
  * [Using GitPack](#using-gitpack)
  * [From AUR](#from-aur)
* [Usage](#usage)
  * [Custom temperatures](#custom-temperatures)
* [Thanks](#thanks)
* [Contributing](#contributing)
* [License](#license)

## Install

### Dependencies

* **systemd** suite
* **acpi_call** kernel module (see below)

### Using GitPack

This project supports [GitPack](https://github.com/dominiksalvet/gitpack). Global installation/update:

```sh
sudo gitpack install github.com/dominiksalvet/asus-fan-control
```

> If your system has `apt-get`, GitPack will install acpi_call automatically.

### From AUR

If you are using Arch Linux or an Arch-based distribution, there is an [AUR package](https://aur.archlinux.org/packages/asus-fan-control) available. Just [install](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) asus-fan-control from AUR. Feel free to also enable starting the asus-fan-control at boot:

```sh
sudo systemctl enable asus-fan-control
```

## Usage

The program should be **executed automatically whenever necessary** to keep the effect of a permanent change. Nevertheless, it is possible to invoke it manually as shown below:

```sh
sudo asus-fan-control
```

### Custom temperatures

The fan speed policy is defined by 8 increasing numbers representing temperature boundaries in degrees Celsius between individual fan speed levels. E.g., UX430UA's default temperatures are `55 60 62 65 68 72 76 80` as shown:

| Speed level | Temperature (C°) |
|-------------|------------------|
| 0 (off)     | 54 and less      |
| 1           | 55 to 59         |
| 2           | 60 to 61         |
| 3           | 62 to 64         |
| 4           | 65 to 67         |
| 5           | 68 to 71         |
| 6           | 72 to 75         |
| 7           | 76 to 79         |
| 8 (max)     | 80 and more      |

To apply your custom temperatures, use the `-set-temps:<numbers>` flag. For example:

```sh
sudo asus-fan-control -set-temps:'45 50 55 60 65 70 75 80'
```

## Thanks

The very core of this project stands on [Aleh Filipovich](https://github.com/afilipovich)'s [observation](https://github.com/daringer/asus-fan/issues/44#issuecomment-307589414).

## Contributing

Do you want to contribute? Do you have any questions? Then the [*CONTRIBUTING.md*](CONTRIBUTING.md) file is here for you.

## License

This project is licensed under the [MIT License](LICENSE).
