---
title: Définition des Options par programmation pour le pilote Access | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57bc9dd31299a70c5c8a2272dd49b577f58b7bb0
ms.sourcegitcommit: 1e28f923cda9436a4395a405ebda5149202f8204
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55044465"
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>Définition d’options par programmation pour le pilote Access

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Taille de mémoire tampon|La taille de la mémoire tampon interne, en kilo-octets, qui est utilisé par Microsoft Access pour transférer des données vers et depuis le disque. La taille de mémoire tampon par défaut est de 2 048 Ko (affiché en tant que 2048). Toute valeur entière divisible par 256 peut être entré.|Pour définir cette option dynamiquement, utilisez le mot clé MAXBUFFERSIZE dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Nom de la source de données|Un nom qui identifie la source de données, telles que la paie ou Personnel.|Pour définir cette option de manière dynamique, utilisez le **DSN** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Base de données|Une source de données Microsoft Access peut être configurée sans sélectionné ou créé une base de données. Si aucune base de données n’est fourni lors de l’installation, l’utilisateur sera invité à choisir un fichier de base de données lors de la connexion à la source de données.|Pour définir cette option de manière dynamique, utilisez le **DBQ** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Description|Une description facultative des données dans la source de données ; par exemple, « date d’embauche, historique de salaire et examen actuel de tous les employés. »|Pour définir cette option de manière dynamique, utilisez le **DESCRIPTION** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Exclusive|Si le **exclusif** est activée, la base de données s’ouvre en mode exclusif et est accessible par un seul utilisateur à la fois. Les performances sont améliorées lors de l’exécution en mode exclusif.|Pour définir cette option de manière dynamique, utilisez le **exclusif** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|ImplicitCommitSync|Détermine comment les modifications apportées en dehors d’une transaction sont écrites dans la base de données. Cette valeur est initialement définie sur « Oui », ce qui signifie que le pilote Microsoft Access attendra les validations dans une transaction interne/implicite pour être terminés.|Cette option est incluse dans le **des Options avancées** boîte de dialogue pour le pilote Microsoft Access.|  
|Délai d’expiration de la page|Spécifie la période de temps, en millisecondes, d’une page (si non utilisé) reste dans la mémoire tampon avant d’être supprimés. Pour le pilote Microsoft Access, la valeur par défaut est 500 millisecondes (0,5 seconde). Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Le délai d’expiration de la page ne peut pas être 0 en raison d’un délai intrinsèque. Le délai d’expiration de la page ne peut pas être inférieure au délai inhérent, même si l’option de délai d’attente de page est définie en dessous de cette valeur.|Pour définir cette option de manière dynamique, utilisez le **PAGETIMEOUT** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le **READONLY** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Base de données système|Le chemin d’accès complet de la base de données du système de Microsoft Access à utiliser avec la base de données Microsoft Access que vous souhaitez accéder.<br /><br /> Cliquez sur le **base de données système** pour sélectionner la base de données système à utiliser. Le pilote ODBC Microsoft Access invite l’utilisateur pour un nom et un mot de passe. Le nom par défaut est Admin et le mot de passe par défaut dans Microsoft Access pour l’utilisateur administrateur est une chaîne vide.<br /><br /> Pour renforcer la sécurité de votre base de données Microsoft Access, créez un nouvel utilisateur pour remplacer l’utilisateur administrateur et de supprimer l’utilisateur administrateur ou modifier les objets auxquels l’utilisateur administrateur a accès.|Pour définir cette option de manière dynamique, utilisez le **SYSTEMDB** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Threads|Le nombre de threads d’arrière-plan pour le moteur à utiliser. Pour le pilote Microsoft Access, cette valeur par défaut est 3, mais peut être modifiée. L’utilisateur peut souhaiter augmenter le nombre de threads s’il existe une grande quantité d’activité dans la base de données.<br /><br /> Cette option est incluse dans le **des Options avancées** boîte de dialogue pour le pilote Microsoft Access.|Pour définir cette option de manière dynamique, utilisez le **THREADS** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|UserCommitSync|Détermine si le pilote Microsoft Access va effectuer des transactions explicites définies par l’utilisateur de façon asynchrone. Cette valeur est initialement définie sur « Oui », ce qui signifie que le pilote Microsoft Access attendra les validations dans une transaction définie par l’utilisateur à effectuer.<br /><br /> Définir cette option sur False permettre avoir des conséquences imprévisibles dans un environnement multi-utilisateur.|Pour définir cette option de manière dynamique, utilisez le **USERCOMMITSYNC** mot clé dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|
