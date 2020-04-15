---
title: Définir des options programmatiquement pour le pilote dBASE (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: 336d0fd4-5448-4d8c-b7d9-49e857228e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 75889d9ff3ccfe01f9b8d5141df7774205522815
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300779"
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>Définition d’options par programmation pour le pilote dBASE

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Nombre de rangées approximative|Détermine si les statistiques de la taille du tableau sont approximatives. Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.|Pour définir cette option de manière dynamique, utilisez le mot clé **STATISTICS** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Séquence de collation|La séquence dans laquelle les champs sont triés.<br /><br /> La séquence peut être : ASCII (la valeur par défaut) ou internationale.|Pour définir cette option de manière dynamique, utilisez le mot clé **COLLATINGSEQUENCE** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Nom de la source de données|Un nom qui identifie la source de données, comme la paie ou le personnel.|Pour définir cette option de manière dynamique, utilisez le mot clé **DSN** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Base de données|Une source de données Microsoft Access peut être configuré sans sélectionner ni créer de base de données. Si aucune base de données n’est fournie lors de la configuration, les utilisateurs seront invités à sélectionner un fichier de base de données lorsqu’ils se connectent à la source de données.|Pour définir cette option de façon dynamique, utilisez le mot clé **DBQ** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Description|Une description facultative des données dans la source de données; par exemple, « La date de location, les antécédents salariaux et l’examen actuel de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **DESCRIPTION** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Exclusif|Si la boîte **exclusive** est sélectionnée, la base de données sera ouverte en mode Exclusif et peut être consultée par un seul utilisateur à la fois. Les performances sont améliorées lorsqu’elles s’exécutent en mode Exclusif.|Pour définir cette option dynamiquement, utilisez le mot clé **EXCLUSIF** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Délai d’attente de page|Spécifie la période de temps, en dixièmes de seconde, qu’une page (si elle n’est pas utilisée) reste dans le tampon avant qu’elle ne soit supprimée. La valeur par défaut est de 600 dixièmes de seconde (60 secondes). Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Le délai d’attente de page ne peut pas être 0 en raison d’un retard inhérent. Le délai d’attente de page ne peut pas être inférieur au délai inhérent, même si l’option de délai d’arrêt de page est définie en dessous de cette valeur.|Pour définir cette option de manière dynamique, utilisez le mot clé **PAGETIMEOUT** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Lecture seule|Désigne la base de données comme lecture seulement.|Pour définir cette option de manière dynamique, utilisez le mot clé **READONLY** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Sélectionnez Directory|Affiche une boîte de dialogue où vous pouvez sélectionner un répertoire qui contient les fichiers auxquels vous souhaitez accéder.<br /><br /> Lorsque vous définissez un répertoire source de données, spécifiez l’annuaire où se trouvent vos fichiers les plus fréquemment utilisés. Le pilote ODBC utilise ce répertoire comme répertoire par défaut. Copiez d’autres fichiers dans cet annuaire s’ils sont fréquemment utilisés. Vous pouvez également qualifier les noms de fichiers dans une déclaration SELECT avec le nom de l’annuaire :<br /><br /> SÉLECTIONNEZ \* À PARTIR DE C: 'MYDIR’EMP<br /><br /> Ou, vous pouvez spécifier un nouvel annuaire par défaut en utilisant la fonction **SQLSetConnectOption** avec l’option SQL_CURRENT_QUALIFIER.|Pour définir cette option de manière dynamique, utilisez le mot clé **DEFAULTDIR** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Afficher les lignes supprimées|Précise si les lignes qui ont été marquées comme supprimées peuvent être récupérées ou positionnées. S’ils sont effacés, les lignes supprimées ne sont pas affichées; s’ils sont sélectionnés, les lignes supprimées sont traitées de la même façon que les lignes non supprimées. Par défaut, cette option est désactivée.|Pour définir cette option de manière dynamique, utilisez le mot clé **DELETED** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|
