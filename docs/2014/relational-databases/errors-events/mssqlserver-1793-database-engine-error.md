---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fdddf626aa081138d58387b9562327964d600074
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869452"
---
# <a name="mssqlserver1793"></a>MSSQLSERVER_1793
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1793|  
|Source de l'événement|MSSQLSERVER|  
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
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
L’exemple ci-dessous réussit, car une clause **MOVE TO** pour les données de base et une clause **FILESTREAM_ON** pour les données FILESTREAM sont spécifiées.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
L’exemple ci-dessous réussit également, car aucune clause **MOVE TO** n’est spécifiée pour les données de base et aucune clause **FILESTREAM_ON** n’est spécifiée pour les données FILESTREAM.  
  
```Transact-SQL  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
