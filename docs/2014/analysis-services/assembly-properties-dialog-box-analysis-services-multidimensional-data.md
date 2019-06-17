---
title: Boîte de dialogue de propriétés assembly (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b21230ddff5a3db043b533a4f921a30b02da739b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66062296"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Propriétés de l'assembly (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Propriétés de l'assembly** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour définir les propriétés d'une référence d'assembly dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Cliquez avec le bouton droit sur un assembly dans **l’Explorateur d’objets** et sélectionnez **Propriétés** pour afficher la boîte de dialogue **Propriétés de l’assembly**.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Nom**|Modifie le nom de la référence de l'assembly.<br /><br /> Remarque : Modification de cette valeur ne modifie pas le nom de l’assembly référencé par la référence d’assembly, mais au lieu de cela modifie le nom utilisé le par le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance ou la base de données lorsque vous faites référence à la référence d’assembly.|  
|**ID**|Affiche l'identificateur de l'assembly référencé par la référence de l'assembly.|  
|**Description**|Modifie la description de la référence de l'assembly.|  
|**Créer un horodateur**|Affiche la date et l'heure de création de la référence de l'assembly.|  
|**Dernière mise à jour du schéma**|Affiche la date et l'heure de la dernière mise à jour de la référence de l'assembly.|  
|**Type**|Affiche le type de la référence de l'assembly. Les valeurs suivantes s'affichent :<br /><br /> **Assembly .NET.** : La référence de l'assembly fait référence à un assembly [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework.<br /><br /> **DLL COM**: La référence de l'assembly fait référence à une bibliothèque COM.|  
|**Source**|Affiche la source de la référence de l'assembly. Cette propriété contient généralement le chemin d'accès et le nom complets de l'assembly référencé par la référence de l'assembly.|  
|**Jeu d’autorisations**|Sélectionnez le jeu d'autorisations utilisé pour déterminer l'accès à la référence de l'assembly. Pour plus d'informations sur les valeurs disponibles pour cette propriété, consultez <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.|  
|**Informations d'emprunt d'identité**|Sélectionnez les informations d'emprunt d'identité à utiliser pour accéder à la référence de l'assembly. Pour plus d’informations sur les valeurs disponibles pour cette propriété, consultez [Élément ImpersonationInfo &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Gestion des assemblys de modèles multidimensionnels](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
