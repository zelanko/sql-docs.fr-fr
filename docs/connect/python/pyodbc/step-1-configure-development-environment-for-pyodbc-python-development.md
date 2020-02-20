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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a1a43540d866faaf79b1c020eb255689862e6d97
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67992520"
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
