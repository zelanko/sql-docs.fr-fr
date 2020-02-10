---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fdddf626aa081138d58387b9562327964d600074
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62869452"
---
# <a name="mssqlserver_1793"></a>MSSQLSERVER_1793
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1793|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|FILESTREAM_BASEDATA_NEED_SAME_PARTITION|  
|Texte du message|Impossible de supprimer l'index '%.*ls' car aucun schéma de partition n'est spécifié pour les données FILESTREAM.|  
  
## <a name="explanation"></a>Explication  
 Ce message apparaît quand vous essayez de supprimer un index cluster sur une table qui contient des données FILESTREAM et que vous spécifiez une clause **MOVE TO** pour les données de base sans spécifier de clause **FILESTREAM_ON** pour les données FILESTREAM.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour supprimer un index cluster sur une table qui contient des données FILESTREAM, utilisez l'une des options suivantes :  
  
-   Spécifiez à la fois une clause **MOVE TO** pour les données de base et une clause **FILESTREAM_ON** pour les données FILESTREAM.  
  
-   Ne spécifiez pas de clause **MOVE TO** pour les données de base ni de clause **FILESTREAM_ON** pour les données FILESTREAM.  
  
 L'exemple suivant échoue car un schéma de partition est spécifié pour les données de base, mais n'est pas spécifié pour les données FILESTREAM.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
 L’exemple ci-dessous réussit, car une clause **MOVE TO** pour les données de base et une clause **FILESTREAM_ON** pour les données FILESTREAM sont spécifiées.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
 L’exemple ci-dessous réussit également, car aucune clause **MOVE TO** n’est spécifiée pour les données de base et aucune clause **FILESTREAM_ON** n’est spécifiée pour les données FILESTREAM.  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
  
