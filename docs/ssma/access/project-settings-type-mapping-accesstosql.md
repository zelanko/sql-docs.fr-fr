---
title: "Paramètres (Type de mappage) du projet (AccessToSQL) | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f1fbca03968ed7257cd7b65a42a6fff5180dbedc
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-type-mapping-accesstosql"></a>Paramètres (Type de mappage) du projet (AccessToSQL)
Les paramètres de mappage de Type de projet vous permettent de définir des mappages de type par défaut pour le projet SSMA. Vous pouvez également spécifier des mappages de type pour les objets de base de données individuels. Pour plus d’informations, consultez [Source de mappage et les Types de données cible](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9).  
  
Mappage de type n’est disponible dans le **les paramètres de projet** et **les paramètres de projet par défaut** boîtes de dialogue :  
  
-   Utilisez le **les paramètres de projet** boîte de dialogue pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de mappage de type, sur le **outils** menu, sélectionnez **les paramètres de projet**, puis cliquez sur **mappage de Type** dans le volet gauche.  
  
-   Utilisez le **les paramètres de projet par défaut** boîte de dialogue pour définir les options de configuration pour tous les projets. Pour accéder aux paramètres de mappage de type, sur le **outils** menu, sélectionnez **les paramètres de projet par défaut**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichés / a été remplacée par **Version cible de la Migration** liste déroulante, puis cliquez sur **mappage de Type** dans le volet gauche.  
  
## <a name="options"></a>Options  
**Type de source**  
Le type de données Access à mapper.  
  
**Type de cible**  
La cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou type de données SQL Azure pour le type de données d’accès spécifié.  
  
Le tableau suivant montre le mappage par défaut entre les types de données source et cible.  
  
|Type de données Access|Type de données de SQL Server|  
|--------------------|------------------------|  
|**binaire [\*... \*]**|**varbinary [\*]**|  
|**boolean**|**bit**|  
|**octets**|**tinyint**|  
|**devise**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**GUID**|**uniqueidentifier**|  
|**entier**|**smallint**|  
|**long**|**int**|  
|**LONGBINARY**|**varbinary(max)**|  
|**Mémo**|**nvarchar(max)**|  
|**Mémo** - pour Access 97|**varchar(max)**|  
|**unique**|**real**|  
|**text[\*..\*]**|**nvarchar [\*]**|  
|**text[\*.. \*]** - pour Access 97|**varchar [\*]**|  
  
**Ajouter**  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
**Modifier**  
Cliquez pour modifier un type de données dans la liste de mappage.  
  
**Supprimer**  
Cliquez pour supprimer le mappage de type de données sélectionnées à partir de la liste de mappage.  
  
**Réinitialiser les valeurs par défaut**  
Cliquez pour réinitialiser tous les mappages de type de données pour les valeurs par défaut SSMA.  
  
## <a name="see-also"></a>Voir aussi  
[Source de mappage et les Types de données cible](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9)  
[Reference(Access) d’Interface utilisateur](http://msdn.microsoft.com/en-us/af24c303-4a41-449b-9c86-d6558a97e839)  
  

