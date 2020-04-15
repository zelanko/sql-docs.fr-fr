---
title: Définir des options programmatiquement pour le pilote Excel (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300769"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Définition d’options par programmation pour le pilote Excel

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Nom de la source de données|Un nom qui identifie la source de données, comme la paie ou le personnel.|Pour définir cette option de manière dynamique, utilisez le mot clé **DSN** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Base de données|Une source de données Microsoft Access peut être configuré sans sélectionner ni créer de base de données. Si aucune base de données n’est fournie lors de la configuration, l’utilisateur sera invité à choisir un fichier de base de données lors de la connexion à la source de données.|Pour définir cette option de façon dynamique, utilisez le mot clé **DBQ** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Description|Une description facultative des données dans la source de données; par exemple, « La date de location, les antécédents salariaux et l’examen actuel de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **DESCRIPTION** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Répertoire|Affiche le répertoire actuellement sélectionné.<br /><br /> Pour les fichiers Microsoft Excel 3.0/4.0, l’affichage du chemin est étiqueté "Directory", tandis que pour les fichiers Microsoft Excel 5.0, 7.0 ou 97, l’affichage du chemin est étiqueté "Workbook".|Pour définir cette option de manière dynamique, utilisez le mot clé **DEFAULTDIR** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Lecture seule|Désigne la base de données comme lecture seulement.|Pour définir cette option de manière dynamique, utilisez le mot clé **READONLY** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Lignes à scanner|Nombre de lignes à numériser pour déterminer le type de données de chaque colonne. Le type de données est déterminé compte tenu du nombre maximum de types de données trouvées. Si des données sont rencontrées qui ne correspondent pas au type de données deviné pour la colonne, le type de données sera retourné comme une valeur NULL.<br /><br /> Pour le pilote Microsoft Excel, vous pouvez entrer un numéro de 1 à 16 pour que les lignes puissent être numérisées. La valeur par défaut à 8; s’il est réglé à 0, toutes les lignes sont numérisées. (Un numéro en dehors de la limite retournera une erreur.)|Pour définir cette option de façon dynamique, utilisez le mot clé **MAXSCANROWS** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Sélectionnez Directory|Affiche une boîte de dialogue où vous pouvez sélectionner un répertoire contenant les fichiers que vous souhaitez accéder.<br /><br /> Lors de la définition d’un répertoire source de données (pour tous les pilotes sauf Microsoft Access), spécifiez l’annuaire où se trouvent vos fichiers les plus couramment utilisés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez d’autres fichiers dans cet annuaire s’ils sont fréquemment utilisés. Vous pouvez également qualifier les noms de fichiers dans une déclaration SELECT avec le nom de l’annuaire :<br /><br /> SÉLECTIONNEZ \* À PARTIR DE C: 'MYDIR’EMP<br /><br /> Ou, vous pouvez spécifier un nouvel annuaire par défaut en utilisant la fonction **SQLSetConnectOption** avec l’option SQL_CURRENT_QUALIFIER.<br /><br /> Pour les fichiers Microsoft Excel 3.0 ou 4.0, l’affichage du chemin est étiqueté "Directory", et le bouton de sélection du chemin est étiqueté "Select Directory". Pour les fichiers Microsoft Excel 5.0, 7.0 ou 97, l’affichage du chemin est étiqueté "Workbook", et le bouton de sélection du chemin est étiqueté "Select Workbook". Lors de la définition d’un répertoire source de données, spécifiez l’annuaire où se trouvent vos fichiers Microsoft Excel les plus couramment utilisés pour Microsoft Excel 3.0/4.0, ou l’annuaire où se trouve le fichier de cahier de travail pour Microsoft Excel 5.0, 7.0 ou 97. **Use Current Directory** est désactivé pour Microsoft Excel 5.0, 7.0 et 97.|Pour définir cette option de manière dynamique, utilisez le mot clé **DEFAULTDIR** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|
