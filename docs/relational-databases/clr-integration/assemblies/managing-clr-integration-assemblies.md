---
title: Gestion des assemblys d’intégration du CLR | Microsoft Docs
description: Vous pouvez héberger des assemblys DLL managés dans SQL Server.  Vous pouvez enregistrer, modifier et supprimer des assemblys, ainsi que gérer les fichiers et autorisations associés.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: f26a05c999a683bacbda6ffc0cb9da23b20595bb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717917"
---
# <a name="managing-clr-integration-assemblies"></a>Gestion des assemblys d'intégration du CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Le code managé est compilé, puis déployé dans des unités appelées « assemblys ». Un assembly est fourni sous la forme d'une DLL ou d'un fichier exécutable (.exe). Alors qu'un fichier exécutable peut s'exécuter seul, une DLL doit être hébergée dans une application existante. Les assemblys DLL managés peuvent être chargés et hébergés par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] exige que vous inscriviez l'assembly dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'instruction CREATE ASSEMBLY avant de pouvoir le charger dans le processus et l'utiliser Les assemblys peuvent également être mis à jour à partir d'une version plus récente au moyen de l'instruction ALTER ASSEMBLY ou supprimés de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec l'instruction DROP ASSEMBLY.  
  
 Les informations d’assembly sont stockées dans la table **sys. assembly_files** de la base de données dans laquelle l’assembly a été installé. La table **sys. assembly_files** contient les colonnes suivantes.  
  
|Colonne|Description|  
|------------|-----------------|  
|assembly_id|Identificateur défini pour l'assembly. Ce numéro est affecté à tous les objets se rapportant au même assembly.|  
|name|Nom de l'objet.|  
|file_id|Nombre identifiant chaque objet, avec le premier objet associé à un **assembly_id** donné qui reçoit la valeur 1. Si plusieurs objets sont associés au même **assembly_id**, chaque valeur de **file_id** suivante est incrémentée de 1.|  
|contenu|Représentation hexadécimale de l'assembly ou du fichier.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d'un assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 Aborde la création des assemblys SAFE, EXTERNAL_ACCESS et UNSAFE CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Modification d'un assembly](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 Décrit la mise à jour des assemblys du CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Suppression d'un assembly](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 Décrit la suppression des assemblys du CLR de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’intégration du CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Sécurité d'accès du code de l'intégration du CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  
