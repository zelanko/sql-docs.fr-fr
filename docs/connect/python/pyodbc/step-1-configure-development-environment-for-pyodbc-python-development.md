---
title: 'Étape 1 : Configurer l’environnement de développement Python pyodbc | Microsoft Docs'
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
manager: craigg
ms.openlocfilehash: e9119883fb96c2ef635cd971f5f598ea625e15d4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732877"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Étape 1 : Configurer l’environnement de développement pour le développement Python pyodbc

## <a name="windows"></a>Windows  
Connectez-vous à la base de données SQL à l’aide de Python - pyodbc sur Windows :
  
1. **Téléchargez le programme d’installation de Python**.  
  Si votre ordinateur ne dispose pas de Python, installez-le. Accédez à la [page de téléchargement de Python](https://www.python.org/downloads/windows/) et téléchargez le programme d’installation approprié. Par exemple, si vous êtes sur un ordinateur 64 bits, téléchargez le programme d’installation de Python 2.7 ou 3.7 (x64).  
  
2. **Installez Python**.  Une fois le programme d’installation est téléchargé, procédez comme suit : un. Double-cliquez sur le fichier pour démarrer le programme d’installation. B. Sélectionnez votre langue, puis acceptez les termes du contrat. c. Suivez les instructions à l’écran et Python doit être installé sur votre ordinateur. d. Vous pouvez vérifier que Python est installé en accédant à `C:\Python27` ou `C:\Python37` et exécutez `python -V` ou `py -V` (pour 3.x) 
      
3. [**Installez Microsoft ODBC Driver for SQL Server sur Windows**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Ouvrez cmd.exe en tant qu’administrateur**     

5. **Installez pyodbc avec pip - Gestionnaire de package Python** (remplacez `C:\Python27\Scripts` avec votre chemin d’accès de Python installée)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Connectez-vous à la base de données SQL à l’aide de Python - pyodbc :
  
1. **Ouvrir terminal**  

2. [**Installer Microsoft ODBC Driver for SQL Server sur Linux**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Installer pyodbc**  
```  
> sudo -H pip install pyodbc
```
