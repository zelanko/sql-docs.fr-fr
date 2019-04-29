---
title: Autres abonnés non-SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 135d317d74a720d51c966ed92f1c305f8c04b838
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63021947"
---
# <a name="other-non-sql-server-subscribers"></a>Autres abonnés non SQL Server
  Pour obtenir la liste des Abonnés non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pris en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)], consultez [Non-SQL Server Subscribers](non-sql-server-subscribers.md). Cette rubrique propose des informations sur la configuration requise des pilotes ODBC et des fournisseurs OLE DB.  
  
## <a name="odbc-driver-requirements"></a>Configuration requise des pilotes ODBC  
 Le pilote ODBC :  
  
-   doit être conforme à ODBC niveau 1 ;  
  
-   doit être thread-safe et adapté à l'architecture de processeur (Intel® ou Alpha) et à la plateforme (32 ou 64 bits) sur lesquelles s'exécute le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ;  
  
-   doit être capable d'exécuter des transactions ;  
  
-   doit prendre en charge le langage de définition de données (DDL - Data Definition Language) ;  
  
-   ne peut pas être en lecture seule ;  
  
-   doit prendre en charge les noms de table longs, tels que **MSreplication_subscriptions**.  
  
## <a name="replicating-using-ole-db-interfaces"></a>Réplication à l'aide d'interfaces OLE DB  
 Les fournisseurs OLE DB doivent prendre en charge les objets suivants pour la réplication transactionnelle :  
  
-   Objet**DataSource**   
  
-   Objet**Session**   
  
-   Objet**Command**   
  
-   Objet**Rowset**   
  
-   Objet**Error**   
  
### <a name="datasource-object-interfaces"></a>Interfaces de l'objet DataSource  
 Les interfaces suivantes sont nécessaires pour se connecter à une source de données :  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 Si le fournisseur prend en charge l'interface **IDBInfo** , [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise cette interface pour extraire des informations, telles que le caractère identificateur entre guillemets, la longueur maximale des instructions SQL et le nombre maximal de caractères que peuvent compter les noms de tables et de colonnes.  
  
### <a name="session-object-interfaces"></a>Interfaces de l'objet Session  
 Les interfaces suivantes sont nécessaires :  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### <a name="command-object-interfaces"></a>Interfaces de l'objet Command  
 Les interfaces suivantes sont nécessaires :  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** est nécessaire pour créer des accesseurs de paramètre. Si le fournisseur prend en charge **ColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise cette interface pour déterminer si une colonne est une colonne d'identité.  
  
### <a name="rowset-object-interfaces"></a>Interfaces de l'objet Rowset  
 Les interfaces suivantes sont nécessaires :  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 Une application doit ouvrir un ensemble de lignes sur une table répliquée ayant été créée dans la base de données d'abonnement. **IColumnsInfo** et **IAccessor** sont nécessaires pour accéder aux données de l'ensemble de lignes.  
  
### <a name="error-object-interfaces"></a>Interfaces de l'objet Error  
 Utilisez les interfaces suivantes pour gérer les erreurs :  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 Utilisez **ISQLErrorInfo** si elle est prise en charge par le fournisseur OLE DB.  
  
 Pour plus d'informations, reportez-vous à la documentation qui accompagne votre fournisseur OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)  
  
  
