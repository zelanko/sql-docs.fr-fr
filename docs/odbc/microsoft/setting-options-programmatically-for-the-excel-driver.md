---
title: Définition d’options par programmation pour le pilote Excel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], setting options programmatically
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1fcd5542e4beee1f7c7a30d5e0ee9f2815a3f0b6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300769"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Définition d’options par programmation pour le pilote Excel

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Nom de la source de données|Nom qui identifie la source de données, telle que la paie ou le personnel.|Pour définir cette option de manière dynamique, utilisez le mot clé **DSN** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Base de données|Une source de données Microsoft Access peut être configurée sans sélectionner ou créer de base de données. Si aucune base de données n’est fournie lors de l’installation, l’utilisateur est invité à choisir un fichier de base de données lors de la connexion à la source de données.|Pour définir cette option de manière dynamique, utilisez le mot clé **DBQ** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Description|Description facultative des données dans la source de données ; par exemple, « date d’embauche, historique des salaires et révision actuelle de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **Description** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Répertoire|Affiche le répertoire actuellement sélectionné.<br /><br /> Pour les fichiers Microsoft Excel 3.0/4.0, l’affichage du chemin d’accès est intitulé « répertoire », tandis que pour les fichiers Microsoft Excel 5,0, 7,0 ou 97, l’affichage du chemin d’accès est intitulé « classeur ».|Pour définir cette option de manière dynamique, utilisez le mot clé **DefaultDir** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le mot clé **ReadOnly** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Lignes à analyser|Nombre de lignes à analyser pour déterminer le type de données de chaque colonne. Le type de données est déterminé en fonction du nombre maximal de types de données trouvés. Si des données qui ne correspondent pas au type de données devinées pour la colonne sont rencontrées, le type de données est retourné en tant que valeur NULL.<br /><br /> Pour le pilote Microsoft Excel, vous pouvez entrer un nombre compris entre 1 et 16 pour les lignes à analyser. La valeur par défaut est 8. Si la valeur est 0, toutes les lignes sont analysées. (Un nombre en dehors de la limite renverra une erreur.)|Pour définir cette option de manière dynamique, utilisez le mot clé **MaxScanRows** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Sélectionner un répertoire|Affiche une boîte de dialogue dans laquelle vous pouvez sélectionner un répertoire contenant les fichiers auxquels vous souhaitez accéder.<br /><br /> Lors de la définition d’un répertoire de source de données (pour tous les pilotes sauf Microsoft Access), spécifiez le répertoire dans lequel se trouvent les fichiers les plus couramment utilisés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez les autres fichiers dans ce répertoire s’ils sont utilisés fréquemment. Vous pouvez également qualifier des noms de fichiers dans une instruction SELECT avec le nom de répertoire :<br /><br /> SÉLECTIONNER \* dans C:\MYDIR\EMP<br /><br /> Vous pouvez également spécifier un nouveau répertoire par défaut à l’aide de la fonction **SQLSetConnectOption** avec l’option SQL_CURRENT_QUALIFIER.<br /><br /> Pour les fichiers Microsoft Excel 3,0 ou 4,0, l’affichage du chemin d’accès est intitulé « répertoire » et le bouton de sélection du chemin d’accès est intitulé « sélectionner le répertoire ». Pour les fichiers Microsoft Excel 5,0, 7,0 ou 97, l’affichage du chemin d’accès est intitulé « classeur » et le bouton de sélection du chemin d’accès est intitulé « sélectionner un classeur ». Lors de la définition d’un répertoire de source de données, spécifiez le répertoire où se trouvent les fichiers Microsoft Excel les plus couramment utilisés pour Microsoft Excel 3.0/4.0, ou le répertoire où se trouve le fichier de classeur pour Microsoft Excel 5,0, 7,0 ou 97. L' **utilisation du répertoire actif** est désactivée pour Microsoft Excel 5,0, 7,0 et 97.|Pour définir cette option de manière dynamique, utilisez le mot clé **DefaultDir** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|
