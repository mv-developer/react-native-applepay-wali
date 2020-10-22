# react-native-applepay-wali

## Getting started

`$ yarn add react-native-applepay-wali`

## Linking

### >= 0.60

Autolinking will just do the job.

### < 0.60

### Mostly automatic installation

`$ react-native link react-native-applepay-wali`

### CocoaPods

Link using [Cocoapods](https://cocoapods.org) by adding this to your `Podfile`:

```ruby
pod 'RNApplePay', :path => '../node_modules/react-native-applepay-wali'
```

### Manual installation

#### iOS

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `react-native-applepay-wali` and add `RNApplePay.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libRNApplePay.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)<

## Usage

```javascript
import { ApplePay } from "react-native-applepay-wali";

const requestData = {
  merchantIdentifier: "merchant.com.example",
  supportedNetworks: ["mastercard", "visa", "mada"],
  countryCode: "SA",
  currencyCode: "SAR",
  paymentSummaryItems: [
    {
      label: "Item label",
      amount: "100.00",
    },
  ],
};

// Check if ApplePay is available
if (ApplePay.canMakePayments) {
  ApplePay.requestPayment(requestData).then((paymentData) => {
    console.log(paymentData);
    // Simulate a request to the gateway
    setTimeout(() => {
      // Show status to user ApplePay.SUCCESS || ApplePay.FAILURE
      ApplePay.complete(ApplePay.SUCCESS).then(() => {
        console.log("completed");
        // do something
      });
    }, 1000);
  });
}
```

## Demo

You can run the demo by cloning the project and running:

`$ yarn demo`
