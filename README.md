# catalogo
import 'package:flutter/material.dart';
import 'package:medina/models/catalog.dart';
import 'package:medina/widgets/itemWidget.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          title: Text("Tortilleria EL EDU"),
          backgroundColor: Colors.orange[400],
        ),
        body: ListView.builder(
            itemCount: CatalogModel.items.length,
            itemBuilder: (context, index) {
              return ItemWidget(item: CatalogModel.items[index]);
            }),
      ),
    );
  }
}

class CatalogModel {
  static final items = [
    Item(id: 1, name: "Tortillas de maiz azul", desc: "Ricas y baratas tortillas azules", price: 16.50, color: "#33505a", image: "https://raw.githubusercontent.com/JaredMedina128/tortilleriaAPP/master/assets/images/T4.jpg"),
    Item(id: 2, name: "Totopos", desc: "Totopos a buen precio", price: 20, color: "#33505a", image: "https://raw.githubusercontent.com/JaredMedina128/tortilleriaAPP/master/assets/images/t5.jpg"),
    Item(id: 3, name: "Tortillas de maiz", desc: "Deliciosas tortillas siempre listas", price: 15, color: "#33505a", image: "https://raw.githubusercontent.com/JaredMedina128/tortilleriaAPP/master/assets/images/t1.jpg"),
  ];
}

class Item {
  final int id;
  final String name;
  final String desc;
  final num price;
  final String color;
  final String image;

  Item({required this.id, required this.name, required this.desc, required this.price, required this.color, required this.image});
}

import 'package:flutter/material.dart';
import 'package:medina/models/catalog.dart';

class ItemWidget extends StatelessWidget {
  final Item item;
  const ItemWidget({Key? key, required this.item}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Padding(
      padding: const EdgeInsets.all(8.0),
      child: Card(
        elevation: 0,
        color: Colors.lime,
        child: Padding(
          padding: const EdgeInsets.all(8.0),
          child: ListTile(
            leading: Image.network(
              item.image,
              height: 90,
              width: 90,
            ),
            title: Padding(
              padding: const EdgeInsets.all(8.0),
              child: Center(child: Text(item.name, style: TextStyle(color: Colors.black, fontWeight: FontWeight.bold, fontSize: 18))),
            ),
            subtitle: Center(child: Text(item.desc, style: TextStyle(color: Colors.indigo.shade500, fontWeight: FontWeight.bold, fontSize: 15))),
            trailing: Text(
              "\$${item.price}",
              style: TextStyle(color: Colors.red[700], fontWeight: FontWeight.bold, fontSize: 20),
            ),
          ),
        ),
      ),
    );
  }
}
