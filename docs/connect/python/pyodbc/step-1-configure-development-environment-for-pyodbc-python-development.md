---
title: 'Étape 1: configurer l’environnement de développement pyodbc python | Microsoft Docs'
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992520"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Python pyodbc

## <a name="windows"></a>Windows  
Se connecter à SQL Database à l’aide de Python-pyodbc sur Windows:
  
1. **Téléchargez le programme d’installation de Python**.  
  Si votre ordinateur ne dispose pas de Python, installez-le. Accédez à la [page de téléchargement de Python](https://www.python.org/downloads/windows/) et téléchargez le programme d’installation approprié. Par exemple, si vous êtes sur un ordinateur 64 bits, téléchargez le programme d’installation de Python 2.7 ou 3.7 (x64).  
  
2. **Installez Python**.  Une fois le programme d’installation téléchargé, procédez comme suit: a. Double-cliquez sur le fichier pour démarrer le programme d’installation. B. Sélectionnez votre langue et acceptez les termes du contrat. c. Suivez les instructions à l’écran et Python doit être installé sur votre ordinateur. d. Vous pouvez vérifier que Python est installé en accédant `C:\Python27` à `C:\Python37` ou à `python -V` et `py -V` exécutez ou (pour 3. x) 
      
3. [**Installez Microsoft ODBC Driver for SQL Server sur Windows**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Ouvrez cmd. exe en tant qu’administrateur**     

5. **Installer pyodbc à l’aide du gestionnaire de package PIP-python** (À `C:\Python27\Scripts` remplacer par le chemin d’accès de Python installé)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Connectez-vous à SQL Database à l’aide de Python-pyodbc:
  
1. **Ouvrir le terminal**  

2. [**Installer Microsoft ODBC Driver for SQL Server sur Linux**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Installer pyodbc**  
```  
> sudo -H pip install pyodbc
```
