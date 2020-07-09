---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 03c60252186a6e8177d379c895ec8eade565a5cd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780197"
---
# <a name="mssqlserver_7711"></a>MSSQLSERVER_7711
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|7711|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PRT_RANGE_OVERLAP|  
|Texte du message|L’option DATA_COMPRESSION a été spécifiée plusieurs fois pour la table, l’index, ou l’une de leurs partitions.|  
  
## <a name="explanation"></a>Explication  
Une erreur s'est produite dans l'option DATA_COMPRESSION dans l'une des instructions suivantes :  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
Si la table ou l'index cité est partitionné, l'option DATA_COMPRESSION a été répertoriée plusieurs fois pour au moins l'une des partitions. Si la table ou l'index n'est pas partitionné, l'option DATA_COMPRESSION a été citée plusieurs fois.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour une table partitionnée ou un index, assurez-vous que l'option DATA_COMPRESSION n'est spécifiée qu'une seule fois pour chaque partition. Pour une table ou un index qui n'est pas partitionné, utilisez l'option DATA_COMPRESSION une seule fois dans l'instruction.  
  
