---
title: Questions fréquentes (FAQ) sur PolyBase | Microsoft Docs
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 0d2afed9961881fe46ae9fcd4ebe2441910deee7
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67730324"
---
# <a name="frequently-asked-questions"></a>Forum aux questions

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

## <a name="polybase-vs-linked-servers"></a>PolyBase et les serveurs liés
Le tableau suivant présente les différences de fonctionnalités entre PolyBase et les serveurs liés :

|PolyBase | Serveurs liés|
|--------------------------|--------------------------|  
|Objet inclus dans l’étendue de la base de données|Objet inclus dans l’étendue de l’instance|
|Utilise des pilotes ODBC|Utilise des fournisseurs OLEDB|
|Prend en charge les opérations en lecture seule pour toutes les sources de données et l’opération d’insertion pour Hadoop et la source de données pool de données uniquement|Prend en charge les opérations de lecture et d’écriture|
|Possibilité de monter en charge les requêtes effectuées sur une source de données distante en une seule connexion |Impossibilité de monter en charge les requêtes effectuées sur une source de données distante en une seule connexion|
|Pushdown de prédicats pris en charge|Pushdown de prédicats pris en charge|
|Pas de configuration distincte nécessaire pour le groupe de disponibilité|Configuration distincte nécessaire pour chaque instance du groupe de disponibilité|
|Authentification de base uniquement|Authentification de base et intégrée|
|Adapté aux requêtes analytiques qui traitent un grand nombre de lignes|Adapté aux requêtes OLTP qui retournent peu de lignes ou une seule|
|Impossibilité de faire participer les requêtes utilisant une table externe aux transactions distribuées|Possibilité de faire participer les requêtes distribuées aux transactions distribuées|

## <a name="whats-new-in-polybase-2019"></a>Nouveautés de PolyBase 2019 

PolyBase dans [!INCLUDE[sssqlv15](../../includes/sssqlv15-md.md)] peut maintenant lire des données provenant d’un plus large éventail de sources de données. Les données de ces sources de données externes peuvent être stockées sous la forme de tables externes sur votre serveur SQL. PolyBase prend également en charge le calcul pushdown sur ces sources de données externes, à l’exception de types génériques ODBC.

### <a name="compatible-data-sources"></a>Sources de données compatibles

- SQL Server
- Oracle
- Teradata
- MongoDB
- Types génériques ODBC compatibles
  
> [!NOTE]
> PolyBase peut autoriser la connexion à des sources de données externes à l’aide de pilotes ODBC tiers. Ces pilotes ne sont pas fournis avec PolyBase et risquent de ne pas fonctionner comme prévu. Pour plus d’informations, voir notre [guide](../../relational-databases/polybase/polybase-configure-odbc-generic.md) relatif à la configuration générique ODBC de PolyBase.  

## <a name="polybase-in-big-data-clusters-vs-polybase-in-stand-alone-instances"></a>Comparaison entre PolyBase dans les clusters Big Data et PolyBase dans les instances autonomes

Le tableau suivant présente les fonctionnalités de PolyBase disponibles dans l’installation autonome de [!INCLUDE[sssqlv15](../../includes/sssqlv15-md.md)] et le cluster Big Data de [!INCLUDE[sssqlv15](../../includes/sssqlv15-md.md)] :

|Fonctionnalité |Cluster Big Data|Instance autonome|
|--------------------------|--------------------------|---------|   
|Créer une source de données externe pour SQL Server, Oracle, Teradata et Mongo DB |X|X |
|Créer une source de données externe à l’aide d’un pilote ODBC tiers compatible | | X|
|Créer une source de données externe pour la source de données Hadoop | X| X|
|Créer une source de données externe pour le Stockage Blob Azure | X| X|
|Créer une table externe sur un pool de données SQL Server | X| |
|Créer une table externe sur un pool de stockage SQL Server | X| |
|Monter en charge l’exécution des requêtes | X| X|

> [!NOTE]
>Le tableau ne décrit pas les fonctionnalités disponibles dans la dernière version de [!INCLUDE[sssqlv15](../../includes/sssqlv15-md.md)] CTP. Pour les connaître, voir les notes de publication. Pour plus d’informations sur les connexions établies avec le connecteur générique ODBC, voir notre [Guide pratique de la configuration des types génériques ODBC](polybase-configure-odbc-generic.md).