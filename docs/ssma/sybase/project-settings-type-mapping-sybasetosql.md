---
title: Paramètres du projet (mappage de Type) (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2698fb3a-f9e6-4e04-94e0-dad289d7ed0a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d7b16bdf3717fa14f91af41663cbd65365eac52a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028663"
---
# <a name="project-settings-type-mapping-sybasetosql"></a>Paramètres du projet (Mappage de type) (SybaseToSQL)
La page mappage de Type de la **paramètres du projet** boîte de dialogue contient les paramètres qui personnalisent comment SSMA convertit les types de données Sybase Adaptive Server Enterprise (ASE) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.  
  
La page mappage de Type est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue.  
  
-   Pour spécifier les paramètres de mappage de type pour tous les futurs projets SSMA, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichés ou a été remplacée par **Version cible de Migration** liste déroulante, puis sélectionnez **le mappage de Type** en bas du volet gauche.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, sélectionnez **paramètres du projet**, puis sélectionnez **le mappage de Type** en bas du volet gauche.  
  
## <a name="options"></a>Options  
**Type de source**  
Le type de données ASE mappé.  
  
**Type de cible**  
La cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données pour le type de données ASE spécifié.  
  
Consultez le tableau dans la section suivante pour la valeur par défaut SSMA pour Sybase les mappage de type.  
  
**Ajouter**  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
**Edition**  
Cliquez pour modifier le type de données sélectionné dans la liste de mappage.  
  
**Supprimer**  
Cliquez pour supprimer le mappage de type de données sélectionnée dans la liste de mappage.  
  
**Rétablir les valeurs par défaut**  
Cliquez pour réinitialiser la liste de mappage de type pour les valeurs par défaut SSMA.  
  
## <a name="default-type-mapping"></a>Mappage de Type par défaut  
Le tableau suivant contient le mappage de type par défaut entre ASE et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données.  
  
|Type de données de l’ASE|Type de données de SQL Server|  
|-----------------|------------------------|  
|**bigint**|**bigint**|  
|**binaire**|**binaire**|  
|**binaire [\*... 8000]**|**binary[\*]**|  
|**binaire [8001..\*]**|**varbinary(max)**|  
|**bit**|**bit**|  
|**char**|**char**|  
|**char varying**|**varchar**|  
|**char varying [\*... 8000]**|**varchar[\*]**|  
|**char varying [8001..\*]**|**varchar(max)**|  
|**Char [\*... 8000]**|**char[\*]**|  
|**Char [8001..\*;]**|**varchar(max)**|  
|**character**|**char**|  
|**variable de caractère**|**varchar**|  
|**variable de caractère [\*... 8000]**|**varchar[\*]**|  
|**variable de caractère [8001..\*]**|**varchar(max)**|  
|**caractère [\*... 8000]**|**char[\*]**|  
|**caractère [8001..\*]**|**varchar(max)**|  
|**date**|**date**|  
|**datetime**|**datetime2[3]**|  
|**dec**|**decimal**|  
|**dec[\*..\*]**|**decimal[\*]**|  
|**dec[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**decimal**|**decimal**|  
|**decimal[\*..\*]**|**decimal[\*]**|  
|**decimal[\*..\*][\*..\*]**|**decimal[\*][\*]**|  
|**double précision**|**float[53]**|  
|**float**|**float[53]**|  
|**float [\*... 15]**|**float[24]**|  
|**float [16..\*]**|**float[53]**|  
|**image**|**image**|  
|**int**|**int**|  
|**entier**|**Int**|  
|**longsysname**|**nvarchar[255]**|  
|**money**|**money**|  
|**national char**|**nchar**|  
|**national char [\*... 4000]**|**nchar[\*]**|  
|**national char varying**|**nvarchar**|  
|**national char varying [\*... 4000]**|**nvarchar[\*]**|  
|**national char varying [4001..\*]**|**nvarchar(max)**|  
|**national char [4001..\*]**|**nvarchar(max)**|  
|**caractères nationaux**|**nchar**|  
|**les caractères nationaux [\*... 4000]**|**nchar[\*]**|  
|**les caractères nationaux [4001..\*]**|**nvarchar(max)**|  
|**variable de caractères nationaux**|**nvarchar**|  
|**variable de caractères nationaux [\*... 4000]**|**nvarchar[\*]**|  
|**variable de caractères nationaux [4001..\*]**|**nvarchar(max)**|  
|**national varchar**|**nvarchar**|  
|**national varchar [\*... 4000]**|**nvarchar[\*]**|  
|**national varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**NCHAR varying**|**nvarchar**|  
|**NCHAR varying [\*... 4000]**|**nvarchar[\*]**|  
|**NCHAR varying [4001..\*]**|**nvarchar(max)**|  
|**NCHAR [\*... 4000]**|**nchar[\*]**|  
|**NCHAR [4001..\*]**|**nvarchar(max)**|  
|**numeric**|**numeric**|  
|**numérique [\*... \*]**|**numeric[\*]**|  
|**numérique [\*... \*][\*.. \*]**|**numeric[\*][\*]**|  
|**nvarchar**|**nvarchar**|  
|**nvarchar[\*..4000]**|**nvarchar[\*]**|  
|**nvarchar[4001..\*]**|**nvarchar(max)**|  
|**real**|**float[24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**smallmoney**|**smallmoney**|  
|**sysname**|**nvarchar[128]**|  
|**sysname[\*..\*]**|**nvarchar[255]**|  
|**texte**|**texte**|  
|**time**|**time[3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**unichar**|**nchar**|  
|**UNICHAR varying**|**nvarchar**|  
|**UNICHAR varying [\*... 4000]**|**nvarchar[\*]**|  
|**UNICHAR varying [4001..\*]**|**nvarchar(max)**|  
|**UNICHAR [\*... 4000]**|**nchar[\*]**|  
|**UNICHAR [4001..\*]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar [\*... 4000]**|**nvarchar[\*]**|  
|**univarchar[4001..\*]**|**nvarchar(max)**|  
|**valeurs bigint non signées**|**numeric[20][0]**|  
|**unsigned int**|**bigint**|  
|**smallint non signé**|**int**|  
|**tinyint non signé**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**varbinary [\*... 8000]**|**varbinary[\*]**|  
|**varbinary [8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**varchar [\*... 8000]**|**varchar[\*]**|  
|**varchar[8001..\*]**|**varchar(max)**|  
  
