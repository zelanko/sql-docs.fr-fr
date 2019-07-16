---
title: Définition des Options par programmation pour le pilote Excel | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 47181fca07aff7b2a0d418b8852cfce47cf9e501
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063522"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Définition d’options par programmation pour le pilote Excel

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Data Source Name|Un nom qui identifie la source de données, telles que la paie ou Personnel.|Pour définir cette option de manière dynamique, utilisez le **DSN** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Base de données|Une source de données Microsoft Access peut être configurée sans sélectionné ou créé une base de données. Si aucune base de données n’est fourni lors de l’installation, l’utilisateur sera invité à choisir un fichier de base de données lors de la connexion à la source de données.|Pour définir cette option de manière dynamique, utilisez le **DBQ** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Description|Une description facultative des données dans la source de données ; par exemple, « date d’embauche, historique de salaire et examen actuel de tous les employés. »|Pour définir cette option de manière dynamique, utilisez le **DESCRIPTION** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Répertoire|Affiche le répertoire actuellement sélectionné.<br /><br /> Pour les fichiers Microsoft Excel 3.0/4.0, l’affichage du chemin d’accès est étiqueté « Directory », tandis que pour Microsoft Excel 5.0, les fichiers 7.0 ou 97, l’affichage du chemin d’accès est étiqueté « Classeur ».|Pour définir cette option de manière dynamique, utilisez le **DEFAULTDIR** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le **READONLY** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Lignes à balayer|Le nombre de lignes à analyser pour déterminer le type de données de chaque colonne. Le type de données est déterminé étant donné le nombre maximal de types de données trouvées. Si les données qui ne correspond pas au type de données estimé pour la colonne sont rencontrées, le type de données sera retourné comme une valeur NULL.<br /><br /> Pour le pilote Microsoft Excel, vous pouvez entrer un nombre compris entre 1 à 16 pour les lignes à balayer. La valeur par défaut est 8 ; Si elle est définie sur 0, toutes les lignes sont analysées. (Un nombre en dehors de la limite retournera une erreur).|Pour définir cette option de manière dynamique, utilisez le **MAXSCANROWS** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Sélectionnez le répertoire|Affiche une boîte de dialogue où vous pouvez sélectionner un répertoire contenant les fichiers que vous souhaitez accéder.<br /><br /> Lorsque vous définissez un répertoire de source de données (pour tous les pilotes à l’exception de Microsoft Access), spécifiez le répertoire où se trouvent vos fichiers couramment utilisés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez les autres fichiers dans ce répertoire si elles sont utilisées fréquemment. Ou bien, vous pouvez qualifier les noms de fichiers dans une instruction SELECT avec le nom du répertoire :<br /><br /> SÉLECTIONNEZ \* À PARTIR DE C:\MYDIR\EMP<br /><br /> Ou, vous pouvez spécifier un répertoire par défaut à l’aide de la **SQLSetConnectOption** fonction avec l’option SQL_CURRENT_QUALIFIER.<br /><br /> Pour Microsoft Excel 3.0 ou 4.0 fichiers, l’affichage du chemin d’accès est intitulé « Directory », et le bouton de sélection du chemin d’accès est étiqueté « Sélectionner un répertoire ». Pour les fichiers Microsoft Excel 5.0, 7.0 ou 97, l’affichage du chemin d’accès est intitulé « Classeur », et le bouton de sélection du chemin d’accès est étiqueté « Sélectionner le classeur ». Lorsque vous définissez un répertoire de source de données, spécifiez le répertoire où vos fichiers Microsoft Excel plus couramment utilisés se trouvent pour Microsoft Excel 3.0/4.0, ou le répertoire où se trouve le fichier de classeur pour Microsoft Excel 5.0, 7.0 ou 97. **Utiliser le répertoire actif** est désactivée pour Microsoft Excel 5.0, 7.0 et 97.|Pour définir cette option de manière dynamique, utilisez le **DEFAULTDIR** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|
