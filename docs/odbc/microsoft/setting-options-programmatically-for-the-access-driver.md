---
title: Définir des options programmatiquement pour le conducteur d’accès ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
ms.assetid: 1690eb71-0cd3-4c00-9e15-f6a3ac5316dd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a90f0a20569a2a0a5bb93dec7aa4b95b50093dc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300789"
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>Définition d’options par programmation pour le pilote Access

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Taille de la mémoire tampon|La taille du tampon interne, en kilooctets, qui est utilisé par Microsoft Access pour transférer des données à l’intérieur et à partir du disque. La taille tampon par défaut est 2048 KB (affiché comme 2048). Toute valeur integer divisible par 256 peut être saisie.|Pour définir cette option de manière dynamique, utilisez le mot clé MAXBUFFERSIZE dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Nom de la source de données|Un nom qui identifie la source de données, comme la paie ou le personnel.|Pour définir cette option de manière dynamique, utilisez le mot clé **DSN** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Base de données|Une source de données Microsoft Access peut être configuré sans sélectionner ni créer de base de données. Si aucune base de données n’est fournie lors de la configuration, l’utilisateur sera invité à choisir un fichier de base de données lors de la connexion à la source de données.|Pour définir cette option de façon dynamique, utilisez le mot clé **DBQ** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Description|Une description facultative des données dans la source de données; par exemple, « La date de location, les antécédents salariaux et l’examen actuel de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **DESCRIPTION** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Exclusif|Si la boîte **exclusive** est sélectionnée, la base de données sera ouverte en mode Exclusif et peut être consultée par un seul utilisateur à la fois. Les performances sont améliorées lors de l’exécution en mode exclusif.|Pour définir cette option dynamiquement, utilisez le mot clé **EXCLUSIF** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|ImpliciteCommitSync|Détermine comment les modifications apportées en dehors d’une transaction sont écrites à la base de données. Cette valeur est initialement définie à "Oui", ce qui signifie que le pilote Microsoft Access attendra que les commits dans une transaction interne / implicite soient complétés.|Cette option est incluse dans la boîte de dialogue **Set Advanced Options** pour le pilote Microsoft Access.|  
|Délai d’attente de page|Spécifie la période de temps, en millisecondes, qu’une page (si elle n’est pas utilisée) reste dans le tampon avant d’être supprimée. Pour le pilote Microsoft Access, la valeur par défaut est de 500 millisecondes (0,5 seconde). Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Le délai d’attente de page ne peut pas être 0 en raison d’un retard inhérent. Le délai d’attente de page ne peut pas être inférieur au délai inhérent, même si l’option de délai d’arrêt de page est définie en dessous de cette valeur.|Pour définir cette option de manière dynamique, utilisez le mot clé **PAGETIMEOUT** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Lecture seule|Désigne la base de données comme lecture seulement.|Pour définir cette option de manière dynamique, utilisez le mot clé **READONLY** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Base de données système|La voie complète de la base de données du système Microsoft Access à utiliser avec la base de données Microsoft Access que vous souhaitez accéder.<br /><br /> Cliquez sur le bouton **Base de données système** pour sélectionner la base de données système à utiliser. Le pilote ODBC Microsoft Access invite l’utilisateur à obtenir un nom et un mot de passe. Le nom par défaut est Admin et le mot de passe par défaut dans Microsoft Access pour l’utilisateur Admin est une chaîne vide.<br /><br /> Pour augmenter la sécurité de votre base de données Microsoft Access, créez un nouvel utilisateur pour remplacer l’utilisateur Admin et supprimez l’utilisateur Admin, ou modifiez les objets auxquels l’utilisateur Admin a accès.|Pour définir cette option de manière dynamique, utilisez le mot clé **SYSTEMDB** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Threads|Le nombre de fils d’arrière-plan pour le moteur à utiliser. Pour le pilote Microsoft Access, cette valeur est par défaut à 3, mais peut être modifiée. L’utilisateur peut vouloir augmenter le nombre de threads s’il y a une grande quantité d’activité dans la base de données.<br /><br /> Cette option est incluse dans la boîte de dialogue **Set Advanced Options** pour le pilote Microsoft Access.|Pour définir cette option de manière dynamique, utilisez le mot clé **THREADS** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|UserCommitSync|Détermine si le pilote Microsoft Access effectuera une transaction explicite définie par l’utilisateur de manière asynchrone. Cette valeur est initialement définie à "Oui", ce qui signifie que le pilote Microsoft Access attendra que les commits dans une transaction définie par l’utilisateur soient complétés.<br /><br /> La définition de cette option à False peut avoir des conséquences imprévisibles dans un environnement multi-utilisateurs.|Pour définir cette option de manière dynamique, utilisez le mot clé **USERCOMMITSYNC** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|
