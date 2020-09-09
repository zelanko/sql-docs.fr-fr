---
description: Informations de référence sur SQL Server Express LocalDB - API d’instance
title: Informations de référence sur l’API d’instance de base de données locale | SQL Server Express Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: faec46da-0536-4de3-96f3-83e607c8a8b6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 892ccbc66070e7ef0d198daba60698502ee3bd0f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541186"
---
# <a name="sql-server-express-localdb-reference---instance-apis"></a>Informations de référence sur SQL Server Express LocalDB - API d’instance
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Dans le monde traditionnel SQL Server basé sur les services, différentes instances de SQL Server installées sur un même ordinateur sont physiquement séparées ; autrement dit, chaque instance doit être installée et supprimée séparément, possède un jeu distinct de binaires, et s'exécute sous un processus de service distinct. Le nom de l'instance SQL Server est utilisé pour spécifier l'instance SQL Server à laquelle l'utilisateur souhaite se connecter.  
  
 L’API SQL Server Express de l’instance de base de données locale utilise un modèle d’instance simplifié et « clair ». Bien que les instances LocalDB individuelles soient séparées sur le disque et dans le Registre, elles utilisent le même jeu de binaires LocalDB partagés. De plus, LocalDB n'utilise pas de services ; les instances de LocalDB sont lancées sur demande par des appels d'API d'instance de LocalDB. Dans LocalDB, le nom de l'instance est utilisé pour spécifier les instances de LocalDB avec lesquelles l'utilisateur souhaite travailler.  
  
 Une instance de base de données locale est toujours la propriété d’un seul utilisateur et est visible et accessible uniquement à partir du contexte de cet utilisateur, sauf si le partage d’instance est activé.  
  
 Bien que techniquement les instances de LocalDB ne soient pas les mêmes que les instances SQL Server traditionnelles, leur utilisation est similaire. Elles sont appelées *instances* pour insister sur cette similarité et les rendre plus intuitives pour SQL Server les utilisateurs.  
  
 LocalDB prend en charge deux types d'instances : les instances automatiques (AI) et les instances nommées (NI). L'identificateur d'une instance de LocalDB est le nom de l'instance.  
  
## <a name="automatic-localdb-instances"></a>Instances automatiques de LocalDB  
 Les instances de base de données locale automatiques sont « publiques ». elles sont créées et gérées automatiquement pour l’utilisateur et peuvent être utilisées par n’importe quelle application. Une instance de base de données locale automatique existe pour chaque version de base de données locale installée sur l’ordinateur de l’utilisateur.  
  
 Les instances automatiques de LocalDB fournissent la gestion transparente d'instances. L'utilisateur n'a pas besoin de créer l'instance. Cela permet aux utilisateurs d'installer facilement des applications et de migrer vers d'autres ordinateurs. Si la version spécifiée de LocalDB est installée sur l'ordinateur, l'instance automatique de LocalDB pour cette version est également disponible sur cet ordinateur.  
  
### <a name="automatic-instance-management"></a>Gestion automatique d'instances  
 Un utilisateur n'a pas besoin de créer une instance automatique de LocalDB. L’instance est créée de manière différée la première fois que l’instance est utilisée, à condition que la version spécifiée de la base de données locale soit disponible sur l’ordinateur de l’utilisateur. Du point de vue de l’utilisateur, l’instance automatique est toujours présente si les binaires de base de données locale sont présents.  
  
 D'autres opérations de gestion d'instances, telles que la suppression, le partage et l'annulation du partage, s'exécutent également pour les instances automatiques. En particulier, la suppression d'une instance automatique réinitialise efficacement l'instance, qui sera recréée lors de l'opération suivante de démarrage. La suppression d'une instance automatique peut être requise si les bases de données système sont endommagées.  
  
### <a name="automatic-instance-naming-rules"></a>Règles de dénomination d'instance automatique  
 Les instances automatiques de LocalDB ont un modèle particulier pour le nom de l'instance qui appartient à un espace de noms réservé. Cela est nécessaire pour éviter des conflits de noms avec les instances nommées de LocalDB.  
  
 Le nom d’instance automatique est le numéro de version de la ligne de base de la base de données locale précédé d’un seul caractère « v ». Cela ressemble à « v » plus deux nombres avec un point entre eux ; par exemple, v 11.0 ou V 12,00.  
  
 Voici des exemples de noms d'instance automatique non conformes :  
  
-   11,0 (absence du caractère « v » au début)  
  
-   v11 (il manque un point et le second numéro de version)  
  
-   v11. (il manque le deuxième numéro de version)  
  
-   v 11.0.1.2 (le numéro de version a plus de deux parties)  
  
## <a name="named-localdb-instances"></a>Instances nommées de LocalDB  
 Les instances de base de données locale nommées sont « privées ». une instance appartient à une seule application chargée de créer et de gérer l’instance. Les instances nommées de LocalDB fournissent l'isolement et améliorent les performances.  
  
### <a name="named-instance-creation"></a>Création d'instance nommée  
 L'utilisateur doit créer des instances nommées explicitement via l'API de gestion de LocalDB, ou implicitement à l'aide du fichier app.config pour une application managée. Une application managée peut également utiliser l'API.  
  
 Chaque instance nommée possède une version associée de LocalDB ; autrement dit, elle indique un jeu de binaires de LocalDB. La version de l'instance nommée est définie pendant le processus de création de l'instance.  
  
### <a name="named-instance-naming-rules"></a>Règles de dénomination d'instance nommée  
 Un nom d’instance de base de données locale peut comporter jusqu’à 128 caractères (la limite est imposée par le type de données **sysname** ). Il s'agit d'une différence importante comparée aux noms d'instances SQL Server traditionnelles, qui sont limités aux noms NetBIOS de 16 caractères ASCII. La raison de cette différence est que la base de données locale traite les bases de données en tant que fichiers et implique donc la sémantique basée sur les fichiers. il est donc intuitif pour les utilisateurs d’avoir plus de liberté dans le choix des noms d’instance.  
  
 Un nom d'instance de LocalDB peut contenir tous les caractères Unicode qui sont valides dans le composant nom de fichier. Les caractères non conformes dans un composant filename sont généralement les suivants : caractères ASCII/Unicode 1 à 31, guillemets ("), inférieur à ( \<), greater than (> ), canal (|), retour arrière (\b), tabulation (\t), deux-points ( :), astérisque (*), point d’interrogation ( ?), barre oblique inverse ( \\ ) et barre oblique (/). Notez que le caractère Null (\0) est autorisé, car il est utilisé pour la fin de chaîne ; tout caractère qui se trouve après le premier caractère NULL est ignoré.  
  
> [!NOTE]  
>  La liste de caractères non conformes peut dépendre du système d'exploitation et peut changer dans les versions ultérieures.  
  
 Les espaces de début et de fin dans les noms d'instances sont ignorés et seront supprimés.  
  
 Pour éviter les conflits de noms, les instances de base de données locale nommées ne peuvent pas avoir un nom qui suit le modèle d’affectation de noms pour les instances automatiques, comme décrit précédemment dans « règles d’affectation automatique des noms d’instance ». Une tentative de création d’une instance nommée avec un nom qui suit le modèle d’affectation de noms d’instance automatique crée effectivement une instance par défaut.  
  
## <a name="sql-server-express-localdb-reference-topics"></a>Rubriques de référence SQL Server Express LocalDB  
 [En-tête et informations de version SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
 Fournit des informations sur le fichier d'en-tête et les clés de Registre pour rechercher l'API d'instance de LocalDB.  
  
 [Outil de gestion en ligne de commande : SqlLocalDB.exe](../../relational-databases/express-localdb-instance-apis/command-line-management-tool-sqllocaldb-exe.md)  
 Décrit SqlLocalDB.exe, un outil de gestion des instances de LocalDB à partir de la ligne de commande.  
  
 [Fonction LocalDBCreateInstance](../../relational-databases/express-localdb-instance-apis/localdbcreateinstance-function.md)  
 Décrit la fonction pour créer une nouvelle instance de LocalDB.  
  
 [Fonction LocalDBDeleteInstance](../../relational-databases/express-localdb-instance-apis/localdbdeleteinstance-function.md)  
 Décrit la fonction pour supprimer une instance de LocalDB.  
  
 [Fonction LocalDBFormatMessage](../../relational-databases/express-localdb-instance-apis/localdbformatmessage-function.md)  
 Décrit la fonction pour retourner la description localisée d'une erreur de LocalDB.  
  
 [Fonction LocalDBGetInstanceInfo](../../relational-databases/express-localdb-instance-apis/localdbgetinstanceinfo-function.md)  
 Décrit la fonction pour obtenir des informations sur une instance de LocalDB, entre autres si elle existe, les informations de version, si elle s'exécute, et ainsi de suite.  
  
 [Fonction LocalDBGetInstances](../../relational-databases/express-localdb-instance-apis/localdbgetinstances-function.md)  
 Décrit la fonction pour retourner toutes les instances de LocalDB avec une version spécifiée.  
  
 [Fonction LocalDBGetVersionInfo](../../relational-databases/express-localdb-instance-apis/localdbgetversioninfo-function.md)  
 Décrit la fonction pour retourner des informations sur une version spécifiée de LocalDB.  
  
 [Fonction LocalDBGetVersions](../../relational-databases/express-localdb-instance-apis/localdbgetversions-function.md)  
 Décrit la fonction pour retourner toutes les versions de LocalDB disponibles sur un ordinateur.  
  
 [Fonction LocalDBShareInstance](../../relational-databases/express-localdb-instance-apis/localdbshareinstance-function.md)  
 Décrit la fonction pour partager une instance spécifiée de LocalDB.  
  
 [Fonction LocalDBStartInstance](../../relational-databases/express-localdb-instance-apis/localdbstartinstance-function.md)  
 Décrit la fonction pour démarrer une instance spécifiée de LocalDB.  
  
 [Fonction LocalDBStartTracing](../../relational-databases/express-localdb-instance-apis/localdbstarttracing-function.md)  
 Décrit la fonction pour activer le suivi d'API pour un utilisateur.  
  
 [Fonction LocalDBStopInstance](../../relational-databases/express-localdb-instance-apis/localdbstopinstance-function.md)  
 Décrit la fonction pour cesser l'exécution d'une instance spécifiée de LocalDB.  
  
 [Fonction LocalDBStopTracing](../../relational-databases/express-localdb-instance-apis/localdbstoptracing-function.md)  
 Décrit la fonction pour désactiver le suivi d'API pour un utilisateur.  
  
 [LocalDBUnshareInstance, fonction](../../relational-databases/express-localdb-instance-apis/localdbunshareinstance-function.md)  
 Décrit la fonction pour cesser le partage d'une instance spécifiée de LocalDB.  
  
  
