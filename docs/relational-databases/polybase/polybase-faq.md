---
title: Questions fréquentes (FAQ) sur PolyBase | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: ''
ms.openlocfilehash: 331ac177831b1e07cfab253c363a35f2bab42a6c
ms.sourcegitcommit: ee76381cfb1c16e0a063315c9c7005f10e98cfe6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072877"
---
# <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

## <a name="polybase-in-big-data-clusters-vs-polybase-in-stand-alone-instances"></a>PolyBase dans les clusters Big Data et PolyBase dans les instances autonomes

|Fonctionnalité |Cluster Big Data| Instance autonome|
|--------------------------|--------------------------|---------|   
|Créer des tables externes| X| X|
|Créer une source de données externe à partir de SQL Server, Oracle, Teradata et Mongo DB |X|X |
|Créer une source de données externe à l’aide d’un pilote ODBC tiers compatible | | X|
|Groupes de scale-out PolyBase | X | |
|Instances de pools de données | X| |
|Instances de pools de stockage| X| |

>[!NOTE]
>
>Pour plus d’informations sur les connexions à l’aide du connecteur générique ODBC, consultez notre [Guide pratique de la configuration des types génériques ODBC](polybase-configure-odbc-generic.md).

## <a name="whats-new-with-polybase-in-sql-server-2019"></a>Nouveautés de PolyBase dans SQL Server 2019 

PolyBase dans SQL Server 2019 peut désormais lire des données à partir d’une plus grande variété de sources de données. Les données de ces sources de données externes peuvent être stockées sous la forme de tables externes sur votre serveur SQL. PolyBase prend également en charge le calcul pushdown sur ces sources de données externes, à l’exception de types génériques ODBC. 

### <a name="compatible-data-sources"></a>Sources de données compatibles

- SQL Server
- Oracle
- Teradata
- MongoDB
- Types génériques ODBC **compatibles**

  > [!NOTE]
  >
  >PolyBase peut autoriser la connexion à des sources de données externes à l’aide de pilotes ODBC tiers. Ces pilotes ne sont pas fournis avec PolyBase et peuvent fonctionner comme prévu. Pour plus d’informations, consultez notre [guide](polybase-configure-odbc-generic.md) relatif à la configuration générique ODBC de PolyBase.  

## <a name="polybase-vs-linked-servers"></a>PolyBase et les serveurs liés

|PolyBase | Serveurs liés|
|--------------------------|--------------------------|  
|Objet inclus dans l’étendue de la base de données|Objet inclus dans l’étendue de l’instance| 
|Utilise des pilotes ODBC|Utilise des fournisseurs OLEDB| 
| Prend uniquement en charge les opérations en lecture seule. Sera développé ultérieurement| Prend uniquement en charge les opérations en lecture seule. Sera développé ultérieurement| 
|Les requêtes peuvent faire l’objet d’un scale-out et le pushdown est pris en charge|Les requêtes sont en monothread et le pushdown est pris en charge|
|Aucune configuration distincte nécessaire pour le groupe de disponibilité AlwaysOn|Configuration distincte nécessaire pour chaque instance du groupe de disponibilité AlwaysOn|
|Authentification de base uniquement. Améliorations dans SQL Server 2019|Authentification de base et intégrée|