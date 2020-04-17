---
title: Gestion des assemblées d’intégration CLR (fr) Microsoft Docs
description: Vous pouvez héberger des assemblages DLL gérés dans SQL Server.  Vous pouvez vous inscrire, modifier et supprimer les assemblages, ainsi gérer les fichiers et les autorisations associés.
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
ms.openlocfilehash: 19b90d7994aa4b75a294f24345d43333d13a22df
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484728"
---
# <a name="managing-clr-integration-assemblies"></a>Gestion des assemblys d'intégration du CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le code managé est compilé, puis déployé dans des unités appelées « assemblys ». Un assembly est fourni sous la forme d'une DLL ou d'un fichier exécutable (.exe). Alors qu'un fichier exécutable peut s'exécuter seul, une DLL doit être hébergée dans une application existante. Les assemblages DLL gérés peuvent être [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]chargés et hébergés par . [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] exige que vous inscriviez l'assembly dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'instruction CREATE ASSEMBLY avant de pouvoir le charger dans le processus et l'utiliser Les assemblys peuvent également être mis à jour à partir d'une version plus récente au moyen de l'instruction ALTER ASSEMBLY ou supprimés de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec l'instruction DROP ASSEMBLY.  
  
 Les informations d’assemblage sont stockées dans la table **sys.assembly_files** dans la base de données où l’assemblage a été installé. La table **sys.assembly_files** contient les colonnes suivantes.  
  
|Colonne|Description|  
|------------|-----------------|  
|assembly_id|Identificateur défini pour l'assembly. Ce numéro est affecté à tous les objets se rapportant au même assembly.|  
|name|Nom de l'objet.|  
|file_id|Un numéro identifiant chaque objet, le premier objet associé à une **assembly_id** donnée étant donné la valeur de 1. Si plusieurs objets sont associés à la même **assembly_id,** alors chaque valeur **file_id** ultérieure est incrémentée par 1.|  
|content|Représentation hexadécimale de l'assembly ou du fichier.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d'un assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 Aborde la création des assemblys SAFE, EXTERNAL_ACCESS et UNSAFE CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Modification d'un assembly](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 Décrit la mise à jour des assemblys du CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Suppression d'un assembly](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 Décrit la suppression des assemblys du CLR de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’intégration CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Sécurité d'accès du code de l'intégration du CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  
