---
title: Définition d’options par programmation pour le pilote Access | Microsoft Docs
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
ms.openlocfilehash: 688716e9b7ba89500a4d2e8a579da42972e43d0c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063556"
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>Définition d’options par programmation pour le pilote Access

|Option|Description|Méthode|  
|------------|-----------------|------------|  
|Taille de la mémoire tampon|Taille de la mémoire tampon interne, en kilo-octets, utilisée par Microsoft Access pour transférer des données vers et depuis le disque. La taille de la mémoire tampon par défaut est de 2048 Ko (affichée sous la forme 2048). Toute valeur entière divisible par 256 peut être entrée.|Pour définir cette option de manière dynamique, utilisez le mot clé MAXBUFFERSIZE dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Data Source Name|Nom qui identifie la source de données, telle que la paie ou le personnel.|Pour définir cette option de manière dynamique, utilisez le mot clé **DSN** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Base de données|Une source de données Microsoft Access peut être configurée sans sélectionner ou créer de base de données. Si aucune base de données n’est fournie lors de l’installation, l’utilisateur est invité à choisir un fichier de base de données lors de la connexion à la source de données.|Pour définir cette option de manière dynamique, utilisez le mot clé **DBQ** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Description|Description facultative des données dans la source de données ; par exemple, « date d’embauche, historique des salaires et révision actuelle de tous les employés ».|Pour définir cette option de manière dynamique, utilisez le mot clé **Description** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Exclusif|Si la case **exclusive** est cochée, la base de données est ouverte en mode exclusif et n’est accessible qu’à un seul utilisateur à la fois. Les performances sont améliorées lors de l’exécution en mode exclusif.|Pour définir cette option de manière dynamique, utilisez le mot clé **exclusive** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|ImplicitCommitSync|Détermine la façon dont les modifications apportées en dehors d’une transaction sont écrites dans la base de données. Cette valeur est initialement définie sur « Oui », ce qui signifie que le pilote Microsoft Access attendra que les validations dans une transaction interne/implicite soient terminées.|Cette option est incluse dans la boîte de dialogue **définir les options avancées** pour le pilote Microsoft Access.|  
|Délai d’attente de la page|Spécifie la durée, en millisecondes, pendant laquelle une page (si elle n’est pas utilisée) reste dans la mémoire tampon avant d’être supprimée. Pour le pilote Microsoft Access, la valeur par défaut est 500 millisecondes (0,5 secondes). Cette option s’applique à toutes les sources de données qui utilisent le pilote ODBC.<br /><br /> Le délai d’attente de la page ne peut pas être égal à 0 en raison d’un délai inhérent. Le délai d’attente de la page ne peut pas être inférieur au délai inhérent, même si l’option délai d’attente de la page est définie sous cette valeur.|Pour définir cette option de manière dynamique, utilisez le mot clé **PAGETIMEOUT** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Lecture seule|Désigne la base de données en lecture seule.|Pour définir cette option de manière dynamique, utilisez le mot clé **ReadOnly** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Base de données système|Le chemin d’accès complet de la base de données système Microsoft Access à utiliser avec la base de données Microsoft Access à laquelle vous souhaitez accéder.<br /><br /> Cliquez sur le bouton **base de données système** pour sélectionner la base de données système à utiliser. Le pilote ODBC Microsoft Access demande à l’utilisateur un nom et un mot de passe. Le nom par défaut est admin et le mot de passe par défaut dans Microsoft Access pour l’utilisateur administrateur est une chaîne vide.<br /><br /> Pour renforcer la sécurité de votre base de données Microsoft Access, créez un nouvel utilisateur pour remplacer l’utilisateur administrateur et supprimez l’utilisateur administrateur, ou modifiez les objets auxquels l’utilisateur administrateur a accès.|Pour définir cette option de manière dynamique, utilisez le mot clé **SYSTEMDB** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Threads|Nombre de threads d’arrière-plan à utiliser par le moteur. Pour le pilote Microsoft Access, cette valeur est définie par défaut sur 3, mais peut être modifiée. L’utilisateur peut souhaiter augmenter le nombre de threads s’il y a une grande quantité d’activité dans la base de données.<br /><br /> Cette option est incluse dans la boîte de dialogue **définir les options avancées** pour le pilote Microsoft Access.|Pour définir cette option de manière dynamique, utilisez le mot clé **Threads** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|UserCommitSync|Détermine si le pilote Microsoft Access effectue des transactions explicites définies par l’utilisateur de manière asynchrone. Cette valeur est initialement définie sur « Oui », ce qui signifie que le pilote Microsoft Access attendra la fin des validations dans une transaction définie par l’utilisateur.<br /><br /> L’affectation de la valeur false à cette option peut avoir des conséquences imprévisibles dans un environnement multi-utilisateur.|Pour définir cette option de manière dynamique, utilisez le mot clé **USERCOMMITSYNC** dans un appel à [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|
