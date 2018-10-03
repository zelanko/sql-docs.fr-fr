---
title: Référence de l’API de l’Instance SQL Server Express LocalDB | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 65a19135038183d3ddc22fa09dfa47f79c343d92
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130649"
---
# <a name="sql-server-express-localdb-instance-api-reference"></a>Guide de référence de l'API d'instance SQL Server Express LocalDB
  Dans le monde traditionnel SQL Server basé sur les services, différentes instances de SQL Server installées sur un même ordinateur sont physiquement séparées ; autrement dit, chaque instance doit être installée et supprimée séparément, possède un jeu distinct de binaires, et s'exécute sous un processus de service distinct. Le nom de l'instance SQL Server est utilisé pour spécifier l'instance SQL Server à laquelle l'utilisateur souhaite se connecter.  
  
 L'API de l'instance de SQL Server Express LocalDB utilise un modèle simplifié d'instance « allégée ». Bien que les instances LocalDB individuelles soient séparées sur le disque et dans le Registre, elles utilisent le même jeu de binaires LocalDB partagés. De plus, LocalDB n'utilise pas de services ; les instances de LocalDB sont lancées sur demande par des appels d'API d'instance de LocalDB. Dans LocalDB, le nom de l'instance est utilisé pour spécifier les instances de LocalDB avec lesquelles l'utilisateur souhaite travailler.  
  
 Une instance de LocalDB est toujours détenue par un seul utilisateur et est visible et accessible uniquement dans le contexte de cet utilisateur, sauf si le partage d'instance est activé.  
  
 Bien que techniquement les instances de LocalDB ne soient pas les mêmes que les instances SQL Server traditionnelles, leur utilisation est similaire. Elles sont appelées *instances* pour souligner cette similarité et à les rendre plus intuitives aux utilisateurs de SQL Server.  
  
 LocalDB prend en charge deux types d'instances : les instances automatiques (AI) et les instances nommées (NI). L'identificateur d'une instance de LocalDB est le nom de l'instance.  
  
## <a name="automatic-localdb-instances"></a>Instances automatiques de LocalDB  
 Les instances automatiques de LocalDB sont « publiques » ; elles sont créées et gérées automatiquement pour l'utilisateur et peuvent être utilisées par n'importe quelle application. Il existe une instance automatique de LocalDB pour chaque version de LocalDB installée sur l'ordinateur de l'utilisateur.  
  
 Les instances automatiques de LocalDB fournissent la gestion transparente d'instances. L'utilisateur n'a pas besoin de créer l'instance. Cela permet aux utilisateurs d'installer facilement des applications et de migrer vers d'autres ordinateurs. Si la version spécifiée de LocalDB est installée sur l'ordinateur, l'instance automatique de LocalDB pour cette version est également disponible sur cet ordinateur.  
  
### <a name="automatic-instance-management"></a>Gestion automatique d'instances  
 Un utilisateur n'a pas besoin de créer une instance automatique de LocalDB. L'instance est immédiatement créée la première fois que l'instance est utilisée, à condition que la version spécifiée de LocalDB soit disponible sur l'ordinateur de l'utilisateur. Du point de vue de l'utilisateur, l'instance automatique est toujours présente si les binaires de LocalDB sont présents.  
  
 D'autres opérations de gestion d'instances, telles que la suppression, le partage et l'annulation du partage, s'exécutent également pour les instances automatiques. En particulier, la suppression d'une instance automatique réinitialise efficacement l'instance, qui sera recréée lors de l'opération suivante de démarrage. La suppression d'une instance automatique peut être requise si les bases de données système sont endommagées.  
  
### <a name="automatic-instance-naming-rules"></a>Règles de dénomination d'instance automatique  
 Les instances automatiques de LocalDB ont un modèle particulier pour le nom de l'instance qui appartient à un espace de noms réservé. Cela est nécessaire pour éviter des conflits de noms avec les instances nommées de LocalDB.  
  
 Le nom de l'instance automatique est le numéro de version Release de base de LocalDB précédé d'un caractère « v ». Il ressembler à « v » plus deux nombres avec un point entre eux ; par exemple, v11.0 ou V12.00.  
  
 Voici des exemples de noms d'instance automatique non conformes :  
  
-   11.0 (il manque le caractère « v » au début)  
  
-   v11 (il manque un point et le second numéro de version)  
  
-   v11. (il manque le deuxième numéro de version)  
  
-   v 11.0.1.2 (le numéro de version a plus de deux parties)  
  
## <a name="named-localdb-instances"></a>Instances nommées de LocalDB  
 Les instances nommées de LocalDB sont « privées » ; une instance appartient à une seule application qui est chargée de créer et de gérer l'instance. Les instances nommées de LocalDB fournissent l'isolement et améliorent les performances.  
  
### <a name="named-instance-creation"></a>Création d'instance nommée  
 L'utilisateur doit créer des instances nommées explicitement via l'API de gestion de LocalDB, ou implicitement à l'aide du fichier app.config pour une application managée. Une application managée peut également utiliser l'API.  
  
 Chaque instance nommée possède une version associée de LocalDB ; autrement dit, elle indique un jeu de binaires de LocalDB. La version de l'instance nommée est définie pendant le processus de création de l'instance.  
  
### <a name="named-instance-naming-rules"></a>Règles de dénomination d'instance nommée  
 Un nom d'instance de LocalDB peut comporter au plus 128 caractères (la limite est imposée par le type de données `sysname`). Il s'agit d'une différence importante comparée aux noms d'instances SQL Server traditionnelles, qui sont limités aux noms NetBIOS de 16 caractères ASCII. Cette différence tient du fait que LocalDB traite les bases de données comme des fichiers, ce qui implique par conséquent une sémantique basée sur des fichiers. Cette sémantique est donc intuitive pour que les utilisateurs aient plus de liberté en choisissant les noms d'instances.  
  
 Un nom d'instance de LocalDB peut contenir tous les caractères Unicode qui sont valides dans le composant nom de fichier. Caractères non conformes dans un composant de nom de fichier incluent généralement les caractères suivants : caractères ASCII/Unicode 1 31 via, ainsi que les guillemets («), inférieur à (\<), supérieur à (>), barre verticale (|), retour arrière (\b), tabulation (\t), deux-points ( :)), astérisque (*) point d’interrogation ( ?), barre oblique inverse (\\) et de la barre oblique (/). Notez que le caractère Null (\0) est autorisé, car il est utilisé pour la fin de chaîne ; tout caractère qui se trouve après le premier caractère NULL est ignoré.  
  
> [!NOTE]  
>  La liste de caractères non conformes peut dépendre du système d'exploitation et peut changer dans les versions ultérieures.  
  
 Les espaces de début et de fin dans les noms d'instances sont ignorés et seront supprimés.  
  
 Pour éviter les conflits de noms, nommés LocalDB instances ne peut pas avoir un nom qui suit le modèle d’affectation de noms pour les instances automatiques, comme décrit précédemment dans « Instance d’affectation de noms règles automatique. » Une tentative de création d’une instance nommée avec un nom qui suit le modèle de dénomination d’instance automatique efficacement crée une instance par défaut.  
  
## <a name="sql-server-express-localdb-reference-topics"></a>Rubriques de référence SQL Server Express LocalDB  
 [En-tête et informations de version de la base de données locale SQL Server Express](sql-server-express-localdb-header-and-version-information.md)  
 Fournit des informations sur le fichier d'en-tête et les clés de Registre pour rechercher l'API d'instance de LocalDB.  
  
 [Outil de gestion en ligne de commande : SqlLocalDB.exe](command-line-management-tool-sqllocaldb-exe.md)  
 Décrit SqlLocalDB.exe, un outil de gestion des instances de LocalDB à partir de la ligne de commande.  
  
 [LocalDBCreateInstance, fonction](localdbcreateinstance-function.md)  
 Décrit la fonction pour créer une nouvelle instance de LocalDB.  
  
 [LocalDBDeleteInstance, fonction](localdbdeleteinstance-function.md)  
 Décrit la fonction pour supprimer une instance de LocalDB.  
  
 [LocalDBFormatMessage, fonction](localdbformatmessage-function.md)  
 Décrit la fonction pour retourner la description localisée d'une erreur de LocalDB.  
  
 [LocalDBGetInstanceInfo, fonction](localdbgetinstanceinfo-function.md)  
 Décrit la fonction pour obtenir des informations sur une instance de LocalDB, entre autres si elle existe, les informations de version, si elle s'exécute, et ainsi de suite.  
  
 [LocalDBGetInstances, fonction](localdbgetinstances-function.md)  
 Décrit la fonction pour retourner toutes les instances de LocalDB avec une version spécifiée.  
  
 [LocalDBGetVersionInfo, fonction](localdbgetversioninfo-function.md)  
 Décrit la fonction pour retourner des informations sur une version spécifiée de LocalDB.  
  
 [LocalDBGetVersions, fonction](localdbgetversions-function.md)  
 Décrit la fonction pour retourner toutes les versions de LocalDB disponibles sur un ordinateur.  
  
 [LocalDBShareInstance, fonction](localdbshareinstance-function.md)  
 Décrit la fonction pour partager une instance spécifiée de LocalDB.  
  
 [LocalDBStartInstance, fonction](localdbstartinstance-function.md)  
 Décrit la fonction pour démarrer une instance spécifiée de LocalDB.  
  
 [LocalDBStartTracing, fonction](localdbstarttracing-function.md)  
 Décrit la fonction pour activer le suivi d'API pour un utilisateur.  
  
 [LocalDBStopInstance, fonction](localdbstopinstance-function.md)  
 Décrit la fonction pour cesser l'exécution d'une instance spécifiée de LocalDB.  
  
 [LocalDBStopTracing, fonction](localdbstoptracing-function.md)  
 Décrit la fonction pour désactiver le suivi d'API pour un utilisateur.  
  
 [LocalDBUnshareInstance, fonction](localdbunshareinstance-function.md)  
 Décrit la fonction pour cesser le partage d'une instance spécifiée de LocalDB.  
  
  
