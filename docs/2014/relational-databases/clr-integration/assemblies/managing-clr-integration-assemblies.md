---
title: Gestion des assemblys d’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
author: rothja
ms.author: jroth
ms.openlocfilehash: f9acc56d72d2ed994f497676813e45ef0a914431
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953779"
---
# <a name="managing-clr-integration-assemblies"></a>Gestion des assemblys d'intégration du CLR
  Le code managé est compilé, puis déployé dans des unités appelées « assemblys ». Un assembly est fourni sous la forme d'une DLL ou d'un fichier exécutable (.exe). Alors qu'un fichier exécutable peut s'exécuter seul, une DLL doit être hébergée dans une application existante. Les assemblys DLL managés peuvent être chargés et hébergés par [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]base de données à l’aide de l’instruction CREATe ASSEMBLy, avant qu’elle ne puisse être chargée dans le processus et utilisée. Les assemblys peuvent également être mis à jour à partir d'une version plus récente au moyen de l'instruction ALTER ASSEMBLY ou supprimés de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec l'instruction DROP ASSEMBLY.  
  
 Les informations relatives aux assemblys sont stockées dans la table `sys.assembly_files`, dans la base de données où l'assembly a été installé. La `sys.assembly_files` table contient les colonnes suivantes.  
  
|Colonne|Description|  
|------------|-----------------|  
|assembly_id|Identificateur défini pour l'assembly. Ce numéro est affecté à tous les objets se rapportant au même assembly.|  
|name|Nom de l'objet.|  
|file_id|Numéro identifiant chaque objet (le premier objet associé à un `assembly_id` possède la valeur 1). Si plusieurs objets sont associés au même `assembly_id`, chaque valeur `file_id` suivante est alors incrémentée de 1.|  
|contenu|Représentation hexadécimale de l'assembly ou du fichier.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d'un assembly](creating-an-assembly.md)  
 Aborde la création des assemblys SAFE, EXTERNAL_ACCESS et UNSAFE CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Modification d'un assembly](altering-an-assembly.md)  
 Décrit la mise à jour des assemblys du CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Suppression d'un assembly](dropping-an-assembly.md)  
 Décrit la suppression des assemblys du CLR de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’intégration du CLR](../security/clr-integration-security.md)   
 [Sécurité d'accès du code de l'intégration du CLR](../security/clr-integration-code-access-security.md)  
  
  
