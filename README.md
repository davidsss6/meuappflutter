# Flutter Demo App

Este é um aplicativo de demonstração criado com Flutter. O objetivo deste projeto é relembrar conceitos e aprender novas funcionalidades do Flutter.

## Funcionalidades

- Exibe um contador que é incrementado quando o botão flutuante é pressionado.
- Permite resetar o contador através de um botão adicional.
- Utiliza um esquema de cores personalizado.

## Alterações Feitas

1. **Alteração da cor da semente**:
    - Alterei a `seedColor` para `Colors.green` no tema do aplicativo.
    
2. **Alteração da cor da AppBar**:
    - Mudei a cor do `AppBar` para `Colors.amber`.
    
3. **Adição de um botão de reset**:
    - Adicionei um botão adicional no corpo do app que reseta o contador.

## Código Fonte

Aqui está o código fonte do aplicativo com as modificações:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.green),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'Flutter Demo Home Page'),
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
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  void _resetCounter() {
    setState(() {
      _counter = 0;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.amber,
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            const Text(
              'Voce apertou o botao este número de vezes',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headlineMedium,
            ),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: _resetCounter,
              child: const Text('Resetar Contador'),
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ),
    );
  }
}
