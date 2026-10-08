# Calculator

A single-file, Arabic-first web calculator styled like an old office adding machine: olive metal body, an LCD display, chunky keys, and a paper-roll history tape.

## Features

- Basic arithmetic: addition, subtraction, multiplication, and division, with standard operator precedence (`36 ÷ 4 + 7` = `16`).
- Percent key (`%`), which works relative to the previous number when used after `+` or `-` (e.g. `1250 + 10 %` adds 10% of 1250).
- Backspace (`⌫`) and clear (`مسح`) keys.
- History tape: the last 30 calculations are kept, and clicking a result loads it back into the display. The tape starts with a few example entries, which are replaced by your first real calculation. You can also clear it with the "clear history" button.
- Digit toggle: switch between Western digits (`123`) and Arabic-Indic digits (`١٢٣`). Your choice is saved in the browser (`localStorage`).
- Right-to-left (RTL) interface in Arabic.
- Error messages for division by zero and invalid operations.
- Responsive layout that works on phones and desktops.

## Getting started

No build step, dependencies, or server are needed.

1. Clone or download this repository.
2. Open `calculator.html` in any modern browser (double-click it, or drag it into a browser window).

An internet connection is optional. It is only used to load the IBM Plex Sans Arabic, JetBrains Mono, and Share Tech Mono fonts from Google Fonts. Without it, the calculator falls back to system fonts.

## Usage

Use the on-screen keys with the mouse or touch, or type on the keyboard:

| Key | Action |
| --- | --- |
| `0`-`9` (also Arabic-Indic `٠`-`٩`) | Enter digits |
| `.` or `,` | Decimal point |
| `+` `-` `*` `/` | Add, subtract, multiply, divide |
| `x` | Multiply |
| `%` | Percent |
| `Enter` or `=` | Calculate |
| `Backspace` | Delete the last digit |
| `Esc` or `Delete` | Clear everything |

## Project structure

| File | Description |
| --- | --- |
| `calculator.html` | The whole app: HTML, CSS, and JavaScript in one file |
| `hello.txt` | A welcome note (Arabic and English) |

## How it works

- Expressions are evaluated with a small shunting-yard parser, so multiplication and division bind tighter than addition and subtraction. It does not use `eval`.
- Results are rounded to 12 significant digits to avoid floating-point noise (e.g. `0.1 + 0.2` shows `0.3`), and very large or very small values switch to exponential notation.
- Input is limited to 15 digits per number.
