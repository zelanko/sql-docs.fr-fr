---
title: Instructions | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d8d6f62a-e815-425c-a80e-a63fd34ec275
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: e6e36b056aaca063970c81d2932ec47ee7cef29e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="transact-sql-statements"></a>Instructions Transact-SQL
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

Cette rubrique récapitule les catégories d’instructions utilisables avec Transact-SQL (T-SQL). Vous trouverez toutes les instructions répertoriées dans le volet de navigation gauche.

## <a name="backup-and-restore"></a>Sauvegarde et restauration
Les instructions de sauvegarde et restauration permettent de créer des sauvegardes et des restauration à partir de sauvegardes.  Pour plus d’informations, consultez la [Vue d’ensemble de la sauvegarde et de la restauration](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).

## <a name="data-definition-language"></a>Data Definition Language
Les instructions DDL (Data Definition Language) définissent des structures de données. Utilisez ces instructions pour créer, modifier ou supprimer des structures de données dans une base de données.
- ALTER
- Classements
- CREATE
- DROP
- DISABLE TRIGGER
- ENABLE TRIGGER
- RENAME
- UPDATE STATISTICS

## <a name="data-manipulation-language"></a>Data Manipulation Language
DML (Data Manipulation Language) affecte les informations stockées dans la base de données. Utilisez ces instructions pour insérer, mettre à jour et modifier les lignes dans la base de données.

- BULK INSERT
- DELETE
- INSERT
- MERGE
- TRUNCATE TABLE

## <a name="permissions-statements"></a>Instructions d’autorisations
Les instructions d’autorisations déterminent les connexions et les utilisateurs qui peuvent accéder aux données et effectuer des opérations. Pour plus d’informations sur l’authentification et l’accès, consultez le [Centre de sécurité](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="service-broker-statements"></a>Instructions de Service Broker
Service Broker est une fonctionnalité qui fournit la prise en charge native des applications de messagerie et de mise en file d’attente. Pour plus d’informations, consultez [Service Broker](../../relational-databases/service-broker/event-notifications.md).

## <a name="session-settings"></a>Paramètres de session
Les instructions SET déterminent comment la session active gère les paramètres au moment de l’exécution. Pour obtenir une vue d’ensemble, consultez [Instructions SET](set-statements-transact-sql.md).
