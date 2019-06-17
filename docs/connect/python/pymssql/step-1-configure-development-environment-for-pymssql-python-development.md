---
title: 'Étape 1 : Configurer l’environnement de développement Python pymssql | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9d74e3ce2f7db91aca295dcb7507431a82e49c8c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803868"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Python pymssql
Vous devez configurer votre environnement de développement avec la configuration requise pour développer une application en utilisant le pilote Python pour SQL Server.    
  
Notez que les pilotes SQL Python utilisent le protocole TDS, qui est activé par défaut dans SQL Server et de la base de données SQL Azure.  Aucune configuration supplémentaire n’est requise.  
  
## <a name="windows"></a>Windows  
  
1. **Installer le runtime Python et le Gestionnaire de package pip**  
A. Accédez à [python.org](https://www.python.org/downloads/)  
B. Cliquez sur le lien de msi du programme d’installation Windows approprié.   
c. Exécuter une fois téléchargé le fichier msi pour installer le runtime Python  
  
2. **Télécharger le module de pymssql** de [ici](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Veillez à que choisir le fichier whl correct.  Par exemple : Si vous utilisez Python 2.7 sur un ordinateur 64 bits : pymssql‑2.1.1‑cp27‑none‑win_amd64.whl. Une fois que vous téléchargez le fichier .whl le placer dans le dossier C:/Python27.  
      
3. **Ouvrez cmd.exe**  
  
4. **Installer le module de pymssql**     
    Par exemple, si vous utilisez Python 2.7 sur un ordinateur 64 bits :  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Installer le runtime Python et le Gestionnaire de package pip** Python est préinstallé sur la plupart des distributions d’Ubuntu.  Si votre ordinateur ne dispose pas de python installée, vous pouvez obtenir à télécharger l’archive tar source à partir de [python.org](https://www.python.org/downloads/) et de créer localement, ou vous pouvez utiliser le Gestionnaire de package :  
```  
> sudo apt-get install python   
```  
  
2.  **Ouvrir terminal**  
  
3.  **Installer les dépendances et le module de pymssql**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installer le runtime Python et le Gestionnaire de package pip**  
A. Accédez à [python.org](https://www.python.org/downloads/)  
B. Cliquez sur le lien de package de programme d’installation Mac approprié.   
c. Exécuter une fois téléchargé le package pour installer le runtime Python  
  
2.  **Ouvrir terminal**  
  
3. **Installer le Gestionnaire de package Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Installer FreeTDS module**  
```  
> brew install FreeTDS  
```  
  
5.  **Installer le module de pymssql**  
```  
> sudo -H pip install pymssql  
```
