---
title: "Autres abonn&#233;s non SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "abonnés non-SQL Server, autres types"
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Autres abonn&#233;s non SQL Server
  Pour obtenir la liste de non -[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abonnés pris en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)], consultez la page [les abonnés non-SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md). Cette rubrique propose des informations sur la configuration requise des pilotes ODBC et des fournisseurs OLE DB.  
  
## Configuration requise des pilotes ODBC  
 Le pilote ODBC :  
  
-   doit être conforme à ODBC niveau 1 ;  
  
-   Doit être un environnement de Serveur de distribution thread-safe.  
  
-   doit être capable d'exécuter des transactions ;  
  
-   doit prendre en charge le langage de définition de données (DDL - Data Definition Language) ;  
  
-   ne peut pas être en lecture seule ;  
  
-   Doit prendre en charge les noms de table longs comme **MSreplication_subscriptions**.  
  
## Réplication à l'aide d'interfaces OLE DB  
 Les fournisseurs OLE DB doivent prendre en charge les objets suivants pour la réplication transactionnelle :  
  
-   **Source de données** objet  
  
-   **Session** objet  
  
-   **Commande** objet  
  
-   **Ensemble de lignes** objet  
  
-   **Erreur** objet  
  
### Interfaces de l'objet DataSource  
 Les interfaces suivantes sont nécessaires pour se connecter à une source de données :  
  
-   **IDBInitialize**  
  
-   **IDBCreateSession**  
  
-   **IDBProperties**  
  
 Si le fournisseur prend en charge la **IDBInfo** interface, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise l’interface pour récupérer des informations telles que le caractère identificateur entre guillemets, la longueur maximale de l’instruction SQL et le nombre maximal de caractères dans les noms de table et de colonne.  
  
### Interfaces de l'objet Session  
 Les interfaces suivantes sont nécessaires :  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### Interfaces de l'objet Command  
 Les interfaces suivantes sont nécessaires :  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** est nécessaire de créer des accesseurs de paramètre. Si le fournisseur prend en charge **IColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilise cette interface pour déterminer si une colonne est une colonne d’identité.  
  
### Interfaces de l'objet Rowset  
 Les interfaces suivantes sont nécessaires :  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 Une application doit ouvrir un ensemble de lignes sur une table répliquée ayant été créée dans la base de données d'abonnement. **IColumnsInfo** et **IAccessor** sont nécessaires pour accéder aux données dans l’ensemble de lignes.  
  
### Interfaces de l'objet Error  
 Utilisez les interfaces suivantes pour gérer les erreurs :  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 Utilisez **ISQLErrorInfo** si elle est prise en charge par le fournisseur OLE DB.  
  
 Pour plus d'informations, reportez-vous à la documentation qui accompagne votre fournisseur OLE DB.  
  
## Voir aussi  
 [Abonnés non-SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)  
  
  