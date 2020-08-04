# React-Native-Sqlite
Criação de um app mobile com react Native e Sqlite

Passos para conectar o banco de dados
-
  1 - instalar as dependências do Sqlite:

      > npm install --save react-native-sqlite-storage

  2 - atualizar as configurações da gradle no arquivo android/settings.gradle:
      
      > ...
      > include ': react-native-sqlite-storage'
      > project(':react-native-sqlite-storage').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-sqlite-storage/src/android')
      > ...
      
  3 - Atualizar app gradle build no arquivo android/app/build.gradle:
  
      > ...
      > dependencies {
      >   ...
      >   compile project(':react-native-sqlite-storage')
      > }
      
  4 - Registrar o pacote react no arquivo android/app/src/main/java/com/nomedoseuapp/MainApplication.java.
  
      > import org.pgsqlite.SQLitePluginPackage;
      
    4.1 - no método getPackages() adicionar esta linha (new SQLitePluginPackage(),):
    
      > @Override
      > protected List<ReactPackage> getPackages(){
      >   return Arrays.<ReactPackage> asList(
      >   new SQLitePluginPackage(), // adicione aqui
      >   new MainReactPackage());
      > }

  5 - Importe no seu App.js o sqlite storage ou por require:
  
      > import SQLite from 'react-native-sqlite-storage';
      
      Ou
      
      > const SQLite = require('react-native-sqlite-storage')
      
  6 - Indicar o seu banco de dados:
  
      > const db = SQLite.openDatabase({name: 'test.db', createFromLocation: '~nomedobd.db'})
      
  7 - Para executar queries use db.transaction:
  
      > db.transaction((tx) => {
      >   tx.executeSql('Select * from tabela', (tx, results) => {
      >     var len = results.rows.length;
      >     if(len > 0) { // if exists
      >       var row = results.rows.item(0); // mostra apenas o primeiro registro
      >     }
      >   });
      > });
