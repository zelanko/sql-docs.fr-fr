---
title: 'Étape 1: configurer l’environnement de développement pymssql python | Microsoft Docs'
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
ms.openlocfilehash: 5bf2942b79cf7e72efbb36a53019de8208cd3b8e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935828"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Python pymssql
Vous devrez configurer votre environnement de développement avec les conditions préalables pour développer une application à l’aide du pilote Python pour SQL Server.    
  
Notez que les pilotes SQL python utilisent le protocole TDS, qui est activé par défaut dans SQL Server et Azure SQL Database.  Aucune configuration supplémentaire n’est requise.  
  
## <a name="windows"></a>Windows  
  
1. **Installer le runtime Python et le gestionnaire de package PIP**  
A. Accédez à [Python.org](https://www.python.org/downloads/)  
B. Cliquez sur le lien MSI approprié pour Windows Installer.   
c. Une fois téléchargé, exécutez le MSI pour installer le runtime python  
  
2. **Télécharger le module pymssql** à partir d' [ici](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Veillez à choisir le fichier WHL approprié.  Par exemple: Si vous utilisez Python 2,7 sur un ordinateur 64 bits, choisissez: pymssql-2.1.1-CP27-None-win_amd64. WHL. Une fois que vous avez téléchargé le fichier. WHL, placez-le dans le dossier C:/Python27.  
      
3. **Ouvrez cmd. exe**  
  
4. **Installer le module pymssql**     
    Par exemple, si vous utilisez Python 2,7 sur un ordinateur 64 bits:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Installer le runtime Python et le gestionnaire de package PIP**  Python est préinstallé sur la plupart des distributions d’Ubuntu.  Si Python n’est pas installé sur votre ordinateur, vous pouvez télécharger la source tarball à partir de [Python.org](https://www.python.org/downloads/) et la générer localement, ou vous pouvez utiliser le gestionnaire de package:  
```  
> sudo apt-get install python   
```  
  
2.  **Ouvrir le terminal**  
  
3.  **Installer le module pymssql et les dépendances**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Installer le runtime Python et le gestionnaire de package PIP**  
A. Accédez à [Python.org](https://www.python.org/downloads/)  
B. Cliquez sur le lien Mac installer pkg approprié.   
c. Une fois téléchargé, exécutez le pkg pour installer le runtime python  
  
2.  **Ouvrir le terminal**  
  
3. **Installer le gestionnaire de package homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Installer le module FreeTDS**  
```  
> brew install FreeTDS  
```  
  
5.  **Installer le module pymssql**  
```  
> sudo -H pip install pymssql  
```
