---
title: 'Étape 1 : Configurer un environnement pour Node.js'
description: Vous devrez configurer votre environnement de développement avec les conditions préalables pour développer une application à l’aide du pilote Node.js pour SQL Server.
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 38337772d9ec9db2503637122d0d1b616dc6ef5f
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528133"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Étape 1 :  Configurer l’environnement de développement pour le développement Node.js
Vous devrez configurer votre environnement de développement avec les conditions préalables pour développer une application à l’aide du pilote Node.js pour SQL Server.  La méthode la plus courante consiste à utiliser le gestionnaire de package Node (npm) pour installer le module fastidieux, mais vous pouvez télécharger le module fastidieux directement sur [GitHub](https://github.com/pekim/tedious) si vous préférez.  
  
Le pilote Node.js utilise le protocole TDS, qui est activé par défaut dans SQL Server et Azure SQL Database.  Aucune configuration supplémentaire n’est nécessaire.  
  
## <a name="windows"></a>Windows  
  
1. **Installez le runtime Node.js et le gestionnaire de package npm.**  
a. Accédez à [Node.js](https://nodejs.org/en/download/)  
b. Cliquez sur le lien msi approprié du programme d'installation Windows.   
c. Une fois le téléchargement effectué, exécutez le fichier msi pour installer Node.js  
  
2. **Ouvrez cmd.exe**  
  
3. **Créez un répertoire de projet** et accédez-y.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Créez un projet Node.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu’à ce que le projet soit créé. À la fin de cette étape, vous devriez voir un fichier package.json dans le répertoire de votre projet.  
```  
> npm init  
```  
  
5. **Installez le module fastidieux dans votre projet.**  Tedious est l’implémentation du protocole TDS, qui sert à communiquer avec SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Ouvrir le terminal**  
  
2. **Installez le runtime Node.js.**  
```  
>sudo apt-get install node  
```  
3. **Installez npm (gestionnaire de package Node).**  
```  
> sudo apt-get install npm  
```  
4. **Créer un répertoire de projet** et y accéder.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Créez un projet Node.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu’à ce que le projet soit créé. À la fin de cette étape, vous devriez voir un fichier package.json dans le répertoire de votre projet.  
```  
> sudo npm init  
```  
  
6. **Installez le module fastidieux dans votre projet.**  Tedious est l’implémentation du protocole TDS, qui sert à communiquer avec SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="macos"></a>macOS  
  
1. **Installez le runtime Node.js et le gestionnaire de package npm.**  
a. Accédez à [Node.js](https://nodejs.org/en/download/)  
b. Cliquez sur le lien approprié du programme d'installation macOS OS.  
c. Une fois le téléchargement effectué, exécutez le fichier dmg pour installer Node.js  
  
2. **Ouvrir le terminal**  
  
3. **Créer un répertoire de projet** et y accéder.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Créez un projet Node.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu’à ce que le projet soit créé. À la fin de cette étape, vous devriez voir un fichier package.json dans le répertoire de votre projet.  
```  
> npm init  
```  
  
5. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS que le pilote utilise pour communiquer avec SQL Server.  
```  
> npm install tedious  
```  
