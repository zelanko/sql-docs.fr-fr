---
title: "Étape 1 : Configurer l’environnement de développement Python pymssql | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: python
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0a1932b41ada3469deed6d36a3c68c3827687cc5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Étape 1 : Configurer l’environnement de développement pour pymssql développement de Python
Vous devez configurer votre environnement de développement avec les composants requis pour développer une application à l’aide du pilote de Python pour SQL Server.    
  
Notez que les pilotes SQL Python utilisent le protocole TDS, qui est activé par défaut dans SQL Server et la base de données SQL Azure.  Aucune configuration supplémentaire n’est requise.  
  
## <a name="windows"></a>Windows  
  
1. **Installer le runtime Python et pip Gestionnaire de package**  
a. Accédez à [python.org](https://www.python.org/downloads/)  
b. Cliquez sur le lien de msi du programme d’installation Windows approprié.   
c. Exécuter une fois téléchargé le fichier msi pour installer le runtime Python  
  
2. **Télécharger le module pymssql** de [ici](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Assurez-vous que vous choisissez le fichier whl correct.  Par exemple : Si vous utilisez Python 2.7 sur un ordinateur 64 bits : pymssql‑2.1.1‑cp27‑none‑win_amd64.whl. Une fois que vous téléchargez le fichier .whl placez-le dans le dossier C:/Python27.  
      
3. **Ouvrez cmd.exe**  
  
4. **Installer le module de pymssql**     
    Par exemple, si vous utilisez Python 2.7 sur un ordinateur 64 bits :  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Installer le runtime Python et Gestionnaire de package de pip** Python est préinstallé sur la plupart des distributions de Ubuntu.  Si votre ordinateur ne dispose pas de python installé, vous pouvez obtenir un téléchargement de l’archive tar de source de [python.org](https://www.python.org/downloads/) et générer localement, ou vous pouvez utiliser le Gestionnaire de package :  
```  
> sudo apt-get install python   
```  
  
2.  **Ouvrez Terminal Server**  
  
3.  **Installer les dépendances et le module de pymssql**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installer le runtime Python et pip Gestionnaire de package**  
a. Accédez à [python.org](https://www.python.org/downloads/)  
b. Cliquez sur le lien de pkg du programme d’installation Mac approprié.   
c. Exécuter une fois téléchargé le pkg pour installer le runtime Python  
  
2.  **Ouvrez Terminal Server**  
  
3. **Installer le Gestionnaire de package Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Installer le module de FreeTDS**  
```  
> brew install FreeTDS  
```  
  
5.  **Installer le module de pymssql**  
```  
> sudo -H pip install pymssql  
```

