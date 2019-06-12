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
manager: jroth
ms.openlocfilehash: 49522e397789c5193ed8f218a5fdf776ba62f001
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799361"
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Node.js
Vous devez configurer votre environnement de développement avec la configuration requise pour développer une application en utilisant le pilote Node.js pour SQL Server.  La méthode la plus courante consiste à utiliser le Gestionnaire de package node (npm) pour installer le module fastidieux, mais vous pouvez télécharger le module fastidieux directement à l’adresse [Github](https://github.com/pekim/tedious) si vous préférez.  
  
Notez que le pilote Node.js utilise le protocole TDS, qui est activé par défaut dans SQL Server et de la base de données SQL Azure.  Aucune configuration supplémentaire n’est requise.  
  
## <a name="windows"></a>Windows  
  
1. **Installer le Gestionnaire de package de runtime et npm Node.js**  
A. Accédez à [Node.js](https://nodejs.org/en/download/)  
B. Cliquez sur le lien de msi du programme d’installation Windows approprié.   
c. Une fois téléchargé, exécutez le fichier msi pour installer Node.js  
  
2. **Ouvrez cmd.exe**  
  
3. **Créez un répertoire de projet** et y accéder.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu'à ce que le projet est créé. À la fin de cette étape, vous devriez voir un fichier package.json dans votre répertoire de projet.  
```  
> npm init  
```  
  
5. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS qui le pilote utilise pour communiquer avec SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Ouvrir terminal**  
  
2. **Installer le runtime Node.js**  
```  
>sudo apt-get install node  
```  
3. **Installez npm (Gestionnaire de package de nœud)**  
```  
> sudo apt-get install npm  
```  
4. **Créez un répertoire de projet** et y accéder.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu'à ce que le projet est créé. À la fin de cette étape, vous devriez voir un fichier package.json dans votre répertoire de projet.  
```  
> sudo npm init  
```  
  
6. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS qui le pilote utilise pour communiquer avec SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installer le Gestionnaire de package de runtime et npm Node.js**  
A. Accédez à [Node.js](https://nodejs.org/en/download/)  
B. Cliquez sur le lien de programme d’installation du système d’exploitation Mac approprié.  
c. Une fois téléchargé, exécutez dmg pour installer Node.js  
  
2. **Ouvrir terminal**  
  
3. **Créez un répertoire de projet** et y accéder.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu'à ce que le projet est créé. À la fin de cette étape, vous devriez voir un fichier package.json dans votre répertoire de projet.  
```  
> npm init  
```  
  
5. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS qui le pilote utilise pour communiquer avec SQL Server.  
```  
> npm install tedious  
```  
  
