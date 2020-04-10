---
title: 'Étape 1 : Configurer l’environnement de développement Python pyodbc | Microsoft Docs'
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dd2063a527d782833f2abfcbd635de30aa27117
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926777"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Python

## <a name="windows"></a>Windows  
Connexion à une base de données SQL à l'aide de Python - pyodbc sur Windows :
  
1. **Téléchargez le programme d’installation de Python**.  
  Si votre ordinateur ne dispose pas de Python, installez-le. Accédez à la [page de téléchargement Python](https://www.python.org/downloads/windows/) et téléchargez le programme d’installation approprié. Par exemple, si vous êtes sur un ordinateur 64 bits, téléchargez le programme d’installation de Python 2.7 ou 3.7 (x64).  
  
2. **Installez Python**.  Une fois le programme d’installation téléchargé, procédez comme suit : a. Pour démarrer le programme d'installation, double-cliquez sur le fichier. b. Sélectionnez votre langue et acceptez les termes du contrat. c. Suivez les instructions à l’écran ; Python devrait être installé sur votre ordinateur. d. Vous pouvez vérifier que Python est installé en accédant à `C:\Python27` ou `C:\Python37`, et en exécutant `python -V` ou `py -V` (pour 3.x) 
      
3. [**Installez Microsoft ODBC Driver for SQL Server sur Windows**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Ouvrez cmd.exe en tant qu’administrateur**     

5. **Installez pyodbc à l’aide du gestionnaire de package pip - Python** (remplacez `C:\Python27\Scripts` par le chemin d’accès de votre installation Python)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Connexion à SQL Database à l’aide de Python - pyodbc :
  
1. **Ouvrir le terminal**  

2. [**Installer Microsoft ODBC Driver for SQL Server sur Linux**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Installer pyodbc**  
```  
> sudo -H pip install pyodbc
```
