# flutter_plugin_scanzy_barcodescanner

flutter_plugin_scanzy_barcodescanner implements the barcode capture capabilities of the ScanzyBarcodeScannerSDK for iOS and Android. It supports reading a large number of different barcode symbologies, such as Code39, Code93, Code128, Codabar, UPC-A, UPC-E, EAN-8, EAN-13, ITF, QRCode, Aztec, PDF-417, Data Matrix, etc.

Learn more with the [documentation](https://developer.scanzy.com) or get started with [sample](https://github.com/ScanzyLLC/scanzy-barcodescanner-sample-flutter)

## Getting Started

#### Install

Add the flutter_plugin_scanzy_barcodescanner plugin to your pubspec.yaml file dependencies:

```yaml
dependencies:
  flutter_plugin_scanzy_barcodescanner: ^0.0.2
```
Then, run this command on your flutter project:
```bash
flutter pub get
```
#### Ready to Use

To use this plugin, in your project, such as lib/main.dart, import the necessary packages:

```dart
import 'package:flutter_plugin_scanzy_barcodescanner/flutter_plugin_scanzy_barcodescanner.dart';
import 'package:flutter_plugin_scanzy_barcodescanner/scanzy_barcode_options.dart';
import 'package:flutter_plugin_scanzy_barcodescanner/scanzy_barcode_format.dart';
import 'package:flutter_plugin_scanzy_barcodescanner/scanzy_barcode_result.dart';
```

Firstly, set the license, it's better to do it in your app's startup, although it's fine to call this function every single time to scan the barcode.

```dart
await ScanzyBarcodescanner.setLicense("your-valid-licensekey");
```

Then, insert below code snippet into the place to scan barcode:

```dart

   //support code128, ean13
   const format = [ScanzyBarcodeFormat.code128, ScanzyBarcodeFormat.ean13];
   
  //enableVibration: true
  //enableBeep: true
  //autoZoom: true
  //scanCropRectOnly: true
   final options = ScanzyBarcodeOptions(format, true, true, true, true);
   ScanzyBarcodeResult result = await ScanzyBarcodescanner.scan(options);

   print(result.barcode);
   print(result.barcodeType);
```

#### API Model

Below gives you more details about the parameters:

The definition of ScanzyBarcodeFormat:

```dart

enum ScanzyBarcodeFormat {
  none,
  code128,
  code39,
  code93,
  codaBar,
  dataMatrix,
  ean13,
  ean8,
  itf,
  qrCode,
  upca,
  upce,
  pdf417,
  aztec,
  maxiCode
}

```
Note: to set the formats you only interested, although you can add ALL formats, it definitely would impact the performance.


The ScanzyBarcodeOptions is defined as:

```dart
class ScanzyBarcodeOptions {
  bool? enableVibration;
  bool? enableBeep;
  bool? autoZoom;
  bool? scanCropRectOnly;
  List<ScanzyBarcodeFormat> formats;

  ScanzyBarcodeOptions(this.formats, this.enableVibration, this.enableBeep,
      this.autoZoom, this.scanCropRectOnly);
}
```
enableVibration: vibrate your phone when barcode detected.<br>

enableBeep: play the beep sound when barcode detected.<br>

autoZoom: the library will zoom in/out automatcially to scan the barcode.<br>

scanRectOnly: only scan the view finder area.<br>

formats: the barcode formats.<br>

## Support

if you have any questions or need help, check out our [official website](https://scanzy.com). Get a free trial license to try. It won't take more than one hour to integrate, insanely simple!
