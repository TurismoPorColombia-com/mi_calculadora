# mi_calculadora
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Mi Calculadora',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const MyHomePage(title: 'Mi Calculadora'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  final _numero1 = TextEditingController();
  final _numero2 = TextEditingController();

  int _suma = 0;

  void _sumar() {
    setState(() {
      _suma = int.parse(_numero1.text) + int.parse(_numero2.text);
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Padding(
        padding: const EdgeInsets.symmetric(horizontal: 8, vertical: 16),
        child: Center(
          child: Column(
            children: <Widget>[
              TextFormField(
                controller: _numero1,
                decoration: const InputDecoration(
                    border: OutlineInputBorder(),
                    labelText: 'Digite el primer numero'),
              ),
              const SizedBox(
                height: 16.0,
              ),
              TextFormField(
                controller: _numero2,
                decoration: const InputDecoration(
                    border: OutlineInputBorder(),
                    labelText: 'Digite el segundo numero'),
              ),
              const SizedBox(
                height: 16.0,
              ),
              ElevatedButton.icon(
                style: TextButton.styleFrom(
                  textStyle: const TextStyle(fontSize: 20),
                  ),
                icon: const Icon(Icons.calculate, size: 20),
                onPressed: () {
                  _sumar();
                },
                label: const Text('Sumar')
              ),
              const SizedBox(
                height: 16.0,
              ),
              Text(
                'La suma es: $_suma',
                style:
                    const TextStyle(fontSize: 20, fontStyle: FontStyle.italic),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
