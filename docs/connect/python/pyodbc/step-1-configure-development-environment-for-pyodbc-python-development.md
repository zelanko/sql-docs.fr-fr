---
title: 'Étape 1 : Configurer l’environnement de développement Python pyodbc | Microsoft Docs'
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f588174ea80677066628cb3e756d7c38bd42fba
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2018
ms.locfileid: "42786884"
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
