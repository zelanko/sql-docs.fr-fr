---
title: 'Étape 1 : Configurer l’environnement de développement pour le développement Node.js | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bce89cc12c7493522de55adffb69fcbe3307cbdf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003758"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Node.js
Vous devrez configurer votre environnement de développement avec les composants requis pour développer une application à l’aide du pilote node. js pour SQL Server.  La méthode la plus courante consiste à utiliser le gestionnaire de package de nœud (NPM) pour installer le module fastidieux, mais vous pouvez télécharger le module fastidieux directement sur [GitHub](https://github.com/pekim/tedious) , si vous le souhaitez.  
  
Notez que le pilote node. js utilise le protocole TDS, qui est activé par défaut dans SQL Server et Azure SQL Database.  Aucune configuration supplémentaire n’est requise.  
  
## <a name="windows"></a>Windows  
  
1. **Installer node. js Runtime et le gestionnaire de package NPM**  
A. Accédez à [node. js](https://nodejs.org/en/download/)  
B. Cliquez sur le lien MSI approprié pour Windows Installer.   
c. Une fois téléchargé, exécutez le fichier MSI pour installer node. js  
  
2. **Ouvrez cmd. exe**  
  
3. **Créez un répertoire de projet** et accédez-y.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu’à ce que le projet soit créé. À la fin de cette étape, vous devriez voir un fichier Package. JSON dans le répertoire de votre projet.  
```  
> npm init  
```  
  
5. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS que le pilote utilise pour communiquer avec SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Ouvrir le terminal**  
  
2. **Installer le runtime node. js**  
```  
>sudo apt-get install node  
```  
3. **Installer NPM (node Package Manager)**  
```  
> sudo apt-get install npm  
```  
4. **Créez un répertoire de projet** et accédez-y.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu’à ce que le projet soit créé. À la fin de cette étape, vous devriez voir un fichier Package. JSON dans le répertoire de votre projet.  
```  
> sudo npm init  
```  
  
6. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS que le pilote utilise pour communiquer avec SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installer node. js Runtime et le gestionnaire de package NPM**  
A. Accédez à [node. js](https://nodejs.org/en/download/)  
B. Cliquez sur le lien Mac OS installer approprié.  
c. Une fois le téléchargement terminé, exécutez le dmg pour installer node. js  
  
2. **Ouvrir le terminal**  
  
3. **Créez un répertoire de projet** et accédez-y.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu’à ce que le projet soit créé. À la fin de cette étape, vous devriez voir un fichier Package. JSON dans le répertoire de votre projet.  
```  
> npm init  
```  
  
5. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS que le pilote utilise pour communiquer avec SQL Server.  
```  
> npm install tedious  
```  
  
