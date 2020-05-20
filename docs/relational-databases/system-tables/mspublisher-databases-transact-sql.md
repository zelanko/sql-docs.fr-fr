---
title: MSpublisher_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpublisher_databases
- MSpublisher_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublisher_databases system table
ms.assetid: 59b0166e-a64c-46b8-befc-c222fa1ccce2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 65d174c38d4d6fe22c73b16af40bcee9d4ff63a3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833106"
---
# <a name="mspublisher_databases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSpublisher_databases** contient une ligne pour chaque paire serveur de publication/base de données de publication desservie par le serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|ID du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**id**|**int**|ID de la ligne.|  
|**publisher_engine_edition**|**int**|Édition du serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], pouvant prendre l'une des valeurs suivantes :<br /><br /> **10** = édition personnelle<br /><br /> **11** = Desktop Engine (MSDE)<br /><br /> **20** = standard<br /><br /> **21** = groupe de travail<br /><br /> **30** = entreprise (évaluation)<br /><br /> **31** = développeur<br /><br /> **40** = Express (Express ne peut pas être un serveur de publication. Cette valeur est présente par souci d'exhaustivité.)|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
