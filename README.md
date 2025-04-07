import React, { useState } from 'react';
import { View, Text, TextInput, TouchableOpacity, StyleSheet, ScrollView } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';

const Stack = createNativeStackNavigator();

function LoginScreen({ navigation }) {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  return (
    <View style={styles.container}>
      <Text style={styles.title}>PoolZap</Text>
      <TextInput style={styles.input} placeholder="Email" value={email} onChangeText={setEmail} />
      <TextInput style={styles.input} placeholder="Senha" secureTextEntry value={password} onChangeText={setPassword} />
      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('Home')}>
        <Text style={styles.buttonText}>Entrar</Text>
      </TouchableOpacity>
      <TouchableOpacity onPress={() => navigation.navigate('Register')}>
        <Text style={styles.link}>Criar conta</Text>
      </TouchableOpacity>
    </View>
  );
}

function RegisterScreen({ navigation }) {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Criar Conta</Text>
      <TextInput style={styles.input} placeholder="Nome" />
      <TextInput style={styles.input} placeholder="Email" />
      <TextInput style={styles.input} placeholder="Senha" secureTextEntry />
      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('Home')}>
        <Text style={styles.buttonText}>Registrar</Text>
      </TouchableOpacity>
    </View>
  );
}

function HomeScreen({ navigation }) {
  return (
    <ScrollView contentContainerStyle={styles.container}>
      <Text style={styles.title}>Bem-vindo ao PoolZap!</Text>
      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('SolicitarServico')}>
        <Text style={styles.buttonText}>Solicitar Limpeza</Text>
      </TouchableOpacity>
      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('ProfissionaisProximos')}>
        <Text style={styles.buttonText}>Profissionais Próximos</Text>
      </TouchableOpacity>
      <TouchableOpacity style={styles.button} onPress={() => navigation.navigate('Historico')}>
        <Text style={styles.buttonText}>Histórico de Serviços</Text>
      </TouchableOpacity>
    </ScrollView>
  );
}

function SolicitarServicoScreen() {
  return (
    <ScrollView contentContainerStyle={styles.container}>
      <Text style={styles.title}>Solicitar Limpeza</Text>
      <TextInput style={styles.input} placeholder="Endereço" />
      <TextInput style={styles.input} placeholder="Tipo de piscina" />
      <TextInput style={styles.input} placeholder="Data desejada (DD/MM/AAAA)" />
      <TouchableOpacity style={styles.button}>
        <Text style={styles.buttonText}>Buscar Profissionais</Text>
      </TouchableOpacity>
    </ScrollView>
  );
}

function ProfissionaisProximosScreen() {
  return (
    <ScrollView contentContainerStyle={styles.container}>
      <Text style={styles.title}>Profissionais Próximos</Text>
      <Text style={styles.text}>[Mapa com localizações em breve]</Text>
      <Text style={styles.text}>João Piscineiro - 4.9 estrelas - WhatsApp: (48) 99999-9999</Text>
    </ScrollView>
  );
}

function HistoricoScreen() {
  return (
    <ScrollView contentContainerStyle={styles.container}>
      <Text style={styles.title}>Histórico de Serviços</Text>
      <Text style={styles.text}>10/03/2025 - Limpeza com João Piscineiro</Text>
      <Text style={styles.text}>22/02/2025 - Manutenção com Água Cristalina</Text>
    </ScrollView>
  );
}

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Login">
        <Stack.Screen name="Login" component={LoginScreen} />
        <Stack.Screen name="Register" component={RegisterScreen} />
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="SolicitarServico" component={SolicitarServicoScreen} />
        <Stack.Screen name="ProfissionaisProximos" component={ProfissionaisProximosScreen} />
        <Stack.Screen name="Historico" component={HistoricoScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}

const styles = StyleSheet.create({
  container: {
    flexGrow: 1,
    padding: 20,
    justifyContent: 'center',
    backgroundColor: '#f0f4ff'
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    marginBottom: 20,
    textAlign: 'center'
  },
  input: {
    backgroundColor: '#fff',
    padding: 10,
    borderRadius: 8,
    marginBottom: 12
  },
  button: {
    backgroundColor: '#007bff',
    padding: 12,
    borderRadius: 8,
    alignItems: 'center',
    marginTop: 10
  },
  buttonText: {
    color: '#fff',
    fontWeight: 'bold'
  },
  link: {
    marginTop: 10,
    color: '#007bff',
    textAlign: 'center'
  },
  text: {
    fontSize: 16,
    marginBottom: 8
  }
});
