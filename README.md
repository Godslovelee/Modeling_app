

# model_sample
creating a modeling profile app,
making use of for loops, and a clear distinction on how to make use of
Backdrop filters in your code

# UI
```dart

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return MaterialApp(
      home: Home(),
    );
  }
}

class Home extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final mediaQuery = MediaQuery.of(context);
    final height = mediaQuery.size.height;
    final width = mediaQuery.size.width;
    // TODO: implement build
    return Stack(children: [
      Image.asset(
        imageplacement,
        fit: BoxFit.fitHeight,
        height: height,
      ),
      Material(
        color: Colors.transparent,
        child: Padding(
          padding: const EdgeInsets.all(15.0),
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Row(
                children: [
                  IconButton(
                    splashColor: Colors.white,
                    icon: Icon(Icons.add_a_photo),
                  ),
                  Spacer(
                    flex: 1,
                  ),
                  IconButton(
                    icon: Icon(Icons.account_circle_rounded),
                  ),
                ],
              ),
              SizedBox(
                height: height / 10,
              ),
              Column(
                children: [
                  //for loop makes its easier to add things to a widget
                  for (var iconButtons in iconButtons) ...[
                    IconButton(
                      focusColor: Colors.deepOrange,
                      icon: Icon(iconButtons.icon),
                    ),
                    Text(iconButtons.text_amount.toString()),
                    Padding(padding: EdgeInsets.all(5.0))
                  ]
                ],
              ),
              Spacer(),
              MyBlurEffect(),
            ],
          ),
        ),
      ),
    ]);
  }
}

class MyBlurEffect extends StatelessWidget {
  //const MyBlurEffect({Key key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    final mediaQuery = MediaQuery.of(context);
    final widths = mediaQuery.size.width;

    return Expanded(
      child: ClipRRect(
        borderRadius: BorderRadius.all(Radius.circular(15)),
        child: Container(
          width: widths,
          child: BackdropFilter(
            filter: ImageFilter.blur(sigmaX: 10.0, sigmaY: 10.0),
            child: Column(children: [
              Text(
                "Jennifer NewGates",
                style: TextStyle(
                    color: Colors.red,
                    fontSize: 23,
                    fontStyle: FontStyle.italic),
                maxLines: 2,
              ),
              Text(
                underlined_text,
                style: TextStyle(fontSize: 15, color: Colors.red),
              ),
              Text(desc, style: TextStyle(fontSize: 15, color: Colors.white)),
              Text(""),
              Text(""),
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children :[
                  ElevatedButton.icon(
                    onPressed: () {},
                    icon: Icon(Icons.add),
                    label: Text("Follow me"),
                  ),
                ]
              )
            ]),
          ),
        ),
      ),
    );
  }
}

const imageplacement = "assets/hair.jpg";

//icon implementation
class IconButtonData {
  final IconData icon;
  // ignore: non_constant_identifier_names
  final int text_amount;

  // ignore: non_constant_identifier_names
  IconButtonData({this.icon, this.text_amount});
}

final List iconButtons = [
  IconButtonData(icon: Icons.message, text_amount: 5),
  IconButtonData(icon: Icons.email, text_amount: 23),
  IconButtonData(icon: Icons.mobile_friendly, text_amount: 31)
];

const desc =
    "Hello my name is jenny, i love to model and advertise for popular brands, it is nice form of art because it lets me express"
    "my soul and feel a sense of tranquility";
const underlined_text = "_______________________________";

```

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://flutter.dev/docs/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://flutter.dev/docs/cookbook)

For help getting started with Flutter, view our
[online documentation](https://flutter.dev/docs), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
