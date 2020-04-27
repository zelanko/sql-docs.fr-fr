---
title: Restaurer à partir de PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f90ea08269e79e57c623af41fc2f0fbc09e2fb42
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66066635"
---
# <a name="restore-from-powerpivot"></a>Restaurer à partir de PowerPivot
  Utilisez la fonctionnalité Restaurer à partir de PowerPivot dans SQL Server Management Studio pour créer une nouvelle base de données model tabulaire sur une instance Analysis Services (exécution en mode tabulaire), ou restaurer une base de données existante dans un classeur PowerPivot (.xlsx).  
  
> [!NOTE]  
>  Le modèle de projet Importer à partir de PowerPivot dans SQL Server Data Tools fournit une fonctionnalité similaire. Pour plus d’informations, consultez [Importer à partir de PowerPivot &#40;des&#41;tabulaires SSAS ](import-from-power-pivot-ssas-tabular.md).  
  
 Lorsque vous utilisez Restaurer à partir de PowerPivot, gardez les points suivants à l'esprit :  
  
-   Pour utiliser Restaurer à partir de PowerPivot, vous devez être connecté en tant que membre du rôle Administrateurs de serveur sur l'instance Analysis Services.  
  
-   Le compte de service de l'instance Analysis Services doit avoir des autorisations de lecture sur le classeur à partir duquel vous effectuez la restauration.  
  
-   Par défaut, lorsque vous restaurez une base de données PowerPivot, la propriété Informations d'emprunt d'identité de source de données de la base de données model tabulaire a la valeur Par défaut, qui indique que le compte de service de l'instance Analysis Services. Nous vous recommandons de modifier les informations d'identification d'emprunt d'identité vers un compte d'utilisateur Windows dans les Propriétés de la base de données. Pour plus d’informations, consultez [Emprunt d’identité &#40;SSAS Tabulaire&#41;](impersonation-ssas-tabular.md).  
  
-   Les données du modèle de données PowerPivot sont copiées dans une base de données model tabulaire existante ou nouvelle sur l'instance Analysis Services. Si votre classeur PowerPivot contient des tables liées, elles seront recréées comme table sans source de données, comme une table créée à l'aide de l'option Coller dans une nouvelle table.  
  
### <a name="to-restore-from-powerpivot"></a>Restaurer à partir de PowerPivot  
  
1.  Dans SSMS, dans l'instance Active Directory à restaurer, cliquez avec le bouton droit sur **Bases de données**, puis cliquez sur **Restaurer à partir de PowerPivot**.  
  
2.  Dans la boîte de dialogue **Restaurer à partir de PowerPivot**, dans **Source de restauration**, dans **Fichier de sauvegarde**, cliquez sur **Parcourir**, puis sélectionnez un fichier .abf ou .xslx à partir duquel effectuer la restauration.  
  
3.  Dans **Destination de la restauration**, dans **Restaurer la base de données**, tapez un nom pour une nouvelle base de données ou une base de données existante. Si vous n'indiquez pas de nom, le nom du classeur est utilisé.  
  
4.  Dans **Emplacement de stockage**, cliquez sur **Parcourir**, puis sélectionnez un emplacement pour stocker la base de données.  
  
5.  Dans **Options**, conservez l'option **Inclure des informations sur la sécurité** activée. Lors de la restauration à partir d'un classeur PowerPivot, ce paramètre ne s'applique pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de données model tabulaires &#40;&#41;SSAS tabulaire](tabular-model-databases-ssas-tabular.md)   
 [Importer à partir de PowerPivot &#40;&#41;tabulaires SSAS](import-from-power-pivot-ssas-tabular.md)  
  
  
