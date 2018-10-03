---
title: La gestion des assemblys d’intégration du CLR | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 1e65bb5c651862a82d78faede158234d20392c1c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48229299"
---
# <a name="managing-clr-integration-assemblies"></a>Gestion des assemblys d'intégration du CLR
  Le code managé est compilé, puis déployé dans des unités appelées « assemblys ». Un assembly est fourni sous la forme d'une DLL ou d'un fichier exécutable (.exe). Alors qu'un fichier exécutable peut s'exécuter seul, une DLL doit être hébergée dans une application existante. Les assemblys DLL managés peuvent être chargées et hébergés par [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données à l’aide de l’instruction CREATE ASSEMBLY, avant de pouvoir être chargé dans le processus et utilisé. Les assemblys peuvent également être mis à jour à partir d'une version plus récente au moyen de l'instruction ALTER ASSEMBLY ou supprimés de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec l'instruction DROP ASSEMBLY.  
  
 Les informations relatives aux assemblys sont stockées dans la table `sys.assembly_files`, dans la base de données où l'assembly a été installé. Le `sys.assembly_files` table contient les colonnes suivantes.  
  
|colonne|Description|  
|------------|-----------------|  
|assembly_id|Identificateur défini pour l'assembly. Ce numéro est affecté à tous les objets se rapportant au même assembly.|  
|NAME|Nom de l'objet.|  
|file_id|Numéro identifiant chaque objet (le premier objet associé à un `assembly_id` possède la valeur 1). Si plusieurs objets sont associés au même `assembly_id`, chaque valeur `file_id` suivante est alors incrémentée de 1.|  
|content|Représentation hexadécimale de l'assembly ou du fichier.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’un assembly](creating-an-assembly.md)  
 Aborde la création des assemblys SAFE, EXTERNAL_ACCESS et UNSAFE CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Modification d’un assembly](altering-an-assembly.md)  
 Décrit la mise à jour des assemblys du CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Suppression d’un assembly](dropping-an-assembly.md)  
 Décrit la suppression des assemblys du CLR de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’intégration du CLR](../security/clr-integration-security.md)   
 [Sécurité d’accès du code d’intégration du CLR](../security/clr-integration-code-access-security.md)  
  
  
