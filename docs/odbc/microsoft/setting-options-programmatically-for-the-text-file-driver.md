---
title: Définir des options programmatiquement pour le pilote de fichiers texte (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e19c3b49479047bc92a7b6f72359d4951d8df16e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300749"
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>Définition d’options par programmation pour le pilote de fichier texte

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Nom de la source de données|Un nom qui identifie la source de données, comme la paie ou le personnel.|Pour définir cette option de manière dynamique, utilisez le mot clé **DSN** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Décrivez Format|Affiche la boîte de dialogue **Définir le format de texte** et vous permet de spécifier le schéma pour les tables individuelles dans le répertoire source de données.|Cette option ne peut pas être définie dynamiquement par un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Description|Une description facultative des données dans la source de données; par exemple, « La date de location, les antécédents salariaux et l’examen actuel de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **DESCRIPTION** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Répertoire|Sélectionne l’annuaire ciblé.|Pour définir cette option de manière dynamique, utilisez le mot clé **DEFAULTDIR** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Liste des extensions|Répertorie les extensions de nom de fichier des fichiers texte sur la source de données. Lorsque le pilote de texte est utilisé, un fichier sans extension est créé lorsque la déclaration CREATE TABLE est exécutée avec un nom qui n’a pas d’extension. D’autres pilotes créent un fichier avec une extension par défaut lorsqu’aucune extension n’est fournie. Pour créer un fichier avec une extension .txt, l’extension doit être incluse dans le nom. Pour afficher des fichiers sans extensions dans la boîte de dialogue **Définir le format de texte,** " ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' doit être ajouté à la liste des extensions.|Pour définir cette option de manière dynamique, utilisez le mot clé **EXTENSIONS** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Lecture seule|Désigne la base de données comme lecture seulement.|Pour définir cette option de manière dynamique, utilisez le mot clé **READONLY** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Lignes à scanner|Nombre de lignes à numériser pour déterminer le type de données de chaque colonne. Le type de données est déterminé compte tenu du nombre maximum de types de données trouvées. Si des données sont rencontrées qui ne correspondent pas au type de données deviné pour la colonne, le type de données sera retourné comme une valeur NULL.<br /><br /> Pour le pilote textuel, vous pouvez saisir un numéro de 1 à 32767 pour le nombre de lignes à numériser; cependant, la valeur sera toujours par défaut à 25. (Un numéro en dehors de la limite retournera une erreur.)|Pour définir cette option de façon dynamique, utilisez le mot clé **MAXSCANROWS** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Sélectionnez Directory|Affiche une boîte de dialogue où vous pouvez sélectionner un répertoire contenant les fichiers que vous souhaitez accéder.<br /><br /> Lors de la définition d’un répertoire source de données spécifier l’annuaire où vos fichiers les plus couramment utilisés sont situés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez d’autres fichiers dans cet annuaire s’ils sont fréquemment utilisés. Vous pouvez également qualifier les noms de fichiers dans une déclaration SELECT avec le nom de l’annuaire :`SELECT * FROM C:\MYDIR\EMP`<br /><br /> Ou, vous pouvez spécifier un nouvel annuaire par défaut en utilisant la fonction **SQLSetConnectOption** avec l’option SQL_CURRENT_QUALIFIER.|Pour définir cette option de manière dynamique, utilisez le mot clé **DEFAULTDIR** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|
