# React-Native-Sqlite
Criação de um app mobile com react Native e Sqlite

Passos para conectar o banco de dados
-
  1 - instalar as dependências do Sqlite:

      > npm install --save react-native-sqlite-storage

  2 - atualizar as configurações da grade(gradle settings):
      
      > include ': react-native-sqlite-storage'
      > project(':react-native-sqlite-storage').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-sqlite-storage/src/android')
