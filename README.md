# Number to Words English

[![pub package](https://img.shields.io/pub/v/number_to_words_english.svg)](https://pub.dev/packages/number_to_words_english)
[![style: very good analysis][very_good_analysis_badge]][very_good_analysis_link]
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[very_good_analysis_badge]: https://img.shields.io/badge/style-very_good_analysis-B22C89.svg
[very_good_analysis_link]: https://pub.dev/packages/very_good_analysis

A Flutter/Dart package that converts numbers to their written words representation with multi-language support.

## Features

✅ **Comprehensive multi-language support**: 12 languages worldwide  
✅ **Extension methods**: Direct conversion with `.toWords()`, `.toFrench()`, etc.  
✅ **Global coverage**: Europe, Asia, Middle East, Latin America  
✅ Convert integers to written words in 12 languages  
✅ Supports numbers from 0 to trillion scale  
✅ Null safety support  
✅ Lightweight and fast  
✅ No external dependencies  
✅ Well tested and documented  
✅ **Backward compatible** - existing code continues to work  
✅ **Modular architecture** - easy to extend with new languages

## Getting started

Add this package to your `pubspec.yaml`:

```yaml
dependencies:
  number_to_words_english: ^3.1.0
```

Then run:

```bash
flutter pub get
```

## Usage

Import the package in your Dart file:

```dart
import 'package:number_to_words_english/number_to_words_english.dart';
```

### Extension Methods (Recommended)

```dart
// Direct number conversion - most convenient!
print(123.toWords()); // English (default)
// Output: 'one hundred twenty-three'

print(123.toVietnamese());
// Output: 'một trăm hai mười ba'

print(123.toSpanish());
// Output: 'ciento veintitrés'

print(123.toFrench());
// Output: 'cent vingt-trois'

print(123.toGerman());
// Output: 'einhundertdreiundzwanzig'

print(123.toChinese());
// Output: '一百二十三'

print(123.toJapanese());
// Output: 'ひゃくにじゅうさん'

print(123.toArabic());
// Output: 'مائة ثلاثة وعشرون'

// Language-specific conversion
print(123.toWordsInLanguage('vi'));
// Output: 'một trăm hai mười ba'

// Integer-specific methods
print(123.toCardinal()); // Cardinal numbers
print(123.canConvertToWords()); // Validation
print(123.wordCount()); // Word count

// Double-specific methods
print(12.34.toWordsWithDecimal());
print(12.34.integerPartToWords()); // Only integer part
print(12.34.decimalPartToWords()); // Only decimal part

// String conversion
print("123.45".toWordsFromString());
print("123".isValidNumberString()); // Validation
```

### Multi-Language API

```dart
// Traditional static method approach
print(NumberToWords.convert('en', 123));
// Output: 'one hundred twenty-three'

print(NumberToWords.convert('vi', 123));
// Output: 'một trăm hai mười ba'

print(NumberToWords.convert('es', 123));
// Output: 'ciento veintitrés'
```

### Supported Languages (12 Total)

| Language Code | Language                | Example (123)            | Region         |
| ------------- | ----------------------- | ------------------------ | -------------- |
| `en`          | English                 | one hundred twenty-three | Global         |
| `vi`          | Vietnamese (Tiếng Việt) | một trăm hai mười ba     | Southeast Asia |
| `es`          | Spanish (Español)       | ciento veintitrés        | Latin America  |
| `fr`          | French (Français)       | cent vingt-trois         | Europe         |
| `de`          | German (Deutsch)        | einhundertdreiundzwanzig | Europe         |
| `it`          | Italian (Italiano)      | centoventitre            | Europe         |
| `pt`          | Portuguese (Português)  | cento e vinte e três     | Latin America  |
| `ru`          | Russian (Русский)       | сто двадцать три         | Eastern Europe |
| `zh`          | Chinese (中文)          | 一百二十三               | East Asia      |
| `ja`          | Japanese (日本語)       | ひゃくにじゅうさん       | East Asia      |
| `nl`          | Dutch (Nederlands)      | honderddrieëntwintig     | Europe         |
| `ar`          | Arabic (العربية)        | مائة ثلاثة وعشرون        | Middle East    |

### Advanced Multi-Language Examples

```dart
// Large numbers in different languages
print(NumberToWords.convert('en', 1000000));
// Output: 'one million'

print(NumberToWords.convert('vi', 1000000));
// Output: 'một triệu'

print(NumberToWords.convert('es', 1000000));
// Output: 'uno millón'

// Negative numbers
print(NumberToWords.convert('en', -123));
// Output: 'minus one hundred twenty-three'

print(NumberToWords.convert('vi', -123));
// Output: 'âm một trăm hai mười ba'

print(NumberToWords.convert('es', -123));
// Output: 'menos ciento veintitrés'

// Decimal numbers
print(NumberToWords.convert('en', 12.34));
// Output: 'twelve point three four'

print(NumberToWords.convert('vi', 12.34));
// Output: 'mười hai phẩy ba tư'

print(NumberToWords.convert('es', 12.34));
// Output: 'doce punto tres cuatro'
```

### Legacy API (Backward Compatible)

The original English-only API continues to work:

```dart
// Legacy API - still supported
print(NumberToWordsEnglish.convert(55));
// Output: 'fifty-five'

print(NumberToWordsEnglish.convert(100000));
// Output: 'one hundred thousand'

print(NumberToWordsEnglish.convert(13578921));
// Output: 'thirteen million five hundred seventy-eight thousand nine hundred twenty-one'
```

### Complete example

```dart
import 'package:flutter/material.dart';
import 'package:number_to_words_english/number_to_words_english.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Number to Words')),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Text(
                'Number: 12345',
                style: TextStyle(fontSize: 24),
              ),
              SizedBox(height: 20),
              Text(
                'Words: ${NumberToWordsEnglish.convert(12345)}',
                style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

## API reference

### NumberToWords (Multi-Language)

#### Methods

##### `static String convert(String languageCode, num number)`

Converts a number to its word representation in the specified language.

**Parameters:**

- `languageCode` (String): Language code ('en', 'vi', 'es')
- `number` (num): The number to convert (int or double)

**Returns:**

- `String`: The word representation of the number in the specified language.

**Example:**

```dart
String result = NumberToWords.convert('vi', 123);
// Returns: "một trăm hai mười ba"
```

##### `static String convertDecimal(String languageCode, String numberStr)`

Converts a decimal number string to words in the specified language.

**Parameters:**

- `languageCode` (String): Language code ('en', 'vi', 'es')
- `numberStr` (String): The number as a string (e.g., "123.45")

**Returns:**

- `String`: The word representation of the decimal number.

##### `static List<String> get supportedLanguages`

Returns a list of supported language codes.

**Returns:**

- `List<String>`: List of language codes ['en', 'vi', 'es']

##### `static Map<String, String> get supportedLanguagesWithNames`

Returns a map of language codes to language names.

**Returns:**

- `Map<String, String>`: Map of language codes to names

##### `static bool isLanguageSupported(String languageCode)`

Checks if a language is supported.

**Parameters:**

- `languageCode` (String): Language code to check

**Returns:**

- `bool`: True if the language is supported

### NumberToWordsEnglish (Legacy)

#### Methods

##### `static String convert(num number)`

Converts a number to its English word representation.

**Note:** This is the legacy API maintained for backward compatibility. For new projects, use `NumberToWords.convert('en', number)` instead.

**Parameters:**

- `number` (num): The number to convert

**Returns:**

- `String`: The English word representation of the number.

**Example:**

```dart
String result = NumberToWordsEnglish.convert(123);
// Returns: "one hundred twenty-three"
```

## Supported range

This package supports converting integers in the following range:

- **Minimum:** 0 (zero)
- **Maximum:** 999,999,999,999,999 (nine hundred ninety-nine trillion nine hundred ninety-nine billion nine hundred ninety-nine million nine hundred ninety-nine thousand nine hundred ninety-nine)

## Additional information

### Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Issues and feedback

Please file issues, bugs, or feature requests in our [issue tracker](https://github.com/kenguyenduc/flutter_number_to_words_english/issues).

### Links

- [Package on pub.dev](https://pub.dev/packages/number_to_words_english)
- [Source code on GitHub](https://github.com/kenguyenduc/flutter_number_to_words_english)
- [Documentation](https://pub.dev/documentation/number_to_words_english/latest/)

## 💖 Support

If you find this package helpful, consider supporting the development:

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://coff.ee/kenguyen)

<details>
<summary>📱 QR Code</summary>

<img src="buymecoffee_qr.png" alt="Buy Me A Coffee QR Code" width="200">

Or visit: [coff.ee/kenguyen](https://coff.ee/kenguyen)

</details>

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2022 Ke Nguyen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
