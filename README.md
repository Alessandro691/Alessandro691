import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Projeto Vila Marimbondo - Criador de Currículos',
      home: CurriculumForm(),
    );
  }
}

class CurriculumForm extends StatefulWidget {
  @override
  _CurriculumFormState createState() => _CurriculumFormState();
}

class _CurriculumFormState extends State<CurriculumForm> {
  final _formKey = GlobalKey<FormState>();
  String name = '';
  String email = '';
  String skills = '';

  void _submitForm() {
    if (_formKey.currentState!.validate()) {
      // Aqui você pode adicionar lógica para salvar o currículo
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('Currículo criado com sucesso!')),
      );
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Projeto Vila Marimbondo - Criador de Currículos'),
      ),
      body: Padding(
        padding: EdgeInsets.all(16.0),
        child: Form(
          key: _formKey,
          child: Column(
            children: <Widget>[
              TextFormField(
                decoration: InputDecoration(labelText: 'Nome'),
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return 'Por favor, insira seu nome';
                  }
                  return null;
                },
                onChanged: (value) {
                  setState(() {
                    name = value;
                  });
                },
              ),
              TextFormField(
                decoration: InputDecoration(labelText: 'Email'),
                validator: (value) {
                  if (value == null || value.isEmpty) {
                    return 'Por favor, insira seu email';
                  }
                  return null;
                },
                onChanged: (value) {
                  setState(() {
                    email = value;
                  });
                },
              ),
              TextFormField(
                decoration: InputDecoration(labelText: 'Habilidades'),
                onChanged: (value) {
                  setState(() {
                    skills = value;
                  });
                },
              ),
              SizedBox(height: 20),
              ElevatedButton(
                onPressed: _submitForm,
                child: Text('Criar Currículo'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
