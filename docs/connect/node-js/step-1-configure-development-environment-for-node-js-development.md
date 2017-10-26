---
title: "Étape 1 : Configurer l’environnement de développement pour le développement de Node.js | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b4e41033ffb30801fd388f7816c34c8a7751daa9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement de Node.js
Vous devez configurer votre environnement de développement avec les composants requis pour développer une application à l’aide du pilote Node.js pour SQL Server.  La méthode la plus courante consiste à utiliser le Gestionnaire de package de nœud (npm) pour installer le module fastidieux, mais vous pouvez télécharger le module fastidieux directement au [Github](https://github.com/pekim/tedious) si vous préférez.  
  
Notez que le pilote Node.js utilise le protocole TDS, qui est activé par défaut dans SQL Server et la base de données SQL Azure.  Aucune configuration supplémentaire n’est requise.  
  
## <a name="windows"></a>Windows  
  
1. **Installer le Gestionnaire de package de runtime et npm Node.js**  
a. Accédez à [Node.js](https://nodejs.org/en/download/)  
b. Cliquez sur le lien de msi du programme d’installation Windows approprié.   
c. Une fois téléchargé, exécutez le fichier msi pour installer Node.js  
  
2. **Ouvrez cmd.exe**  
  
3. **Créer un répertoire de projet** pour y accéder.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu'à ce que le projet est créé. À la fin de cette étape, vous devez voir un fichier package.json dans votre répertoire de projet.  
```  
> npm init  
```  
  
5. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS, qui le pilote utilise pour communiquer avec SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Ouvrez Terminal Server**  
  
2. **Installer le runtime de Node.js**  
```  
>sudo apt-get install node  
```  
3. **Installez npm (Gestionnaire de package de nœud)**  
```  
> sudo apt-get install npm  
```  
4. **Créer un répertoire de projet** pour y accéder.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu'à ce que le projet est créé. À la fin de cette étape, vous devez voir un fichier package.json dans votre répertoire de projet.  
```  
> sudo npm init  
```  
  
6. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS, qui le pilote utilise pour communiquer avec SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installer le Gestionnaire de package de runtime et npm Node.js**  
a. Accédez à [Node.js](https://nodejs.org/en/download/)  
b. Cliquez sur le lien du programme d’installation du système d’exploitation Mac approprié.  
c. Une fois téléchargé, exécutez le dmg pour installer Node.js  
  
2. **Ouvrez Terminal Server**  
  
3. **Créer un répertoire de projet** pour y accéder.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Créez un projet de nœud.**  Pour conserver les valeurs par défaut lors de la création de votre projet, appuyez sur entrée jusqu'à ce que le projet est créé. À la fin de cette étape, vous devez voir un fichier package.json dans votre répertoire de projet.  
```  
> npm init  
```  
  
5. **Installez le module fastidieux dans votre projet.**  Il s’agit de l’implémentation du protocole TDS, qui le pilote utilise pour communiquer avec SQL Server.  
```  
> npm install tedious  
```  
  

