---
title: "Restaurer à partir de PowerPivot | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7beb148b2090fcdcb7a150d3b5eb789beaf7bb08
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="restore-from-power-pivot"></a>Restaurer à partir de PowerPivot
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Vous pouvez utiliser la restauration à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] fonctionnalité dans SQL Server Management Studio pour créer une nouvelle base de données de modèle tabulaire sur une instance d’Analysis Services (exécutée en mode tabulaire), ou pour restaurer une base de données existante à partir d’un [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] classeur (.xlsx).  
  
> [!NOTE]  
>  Le modèle de projet Importer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de SQL Server Data Tools fournit des fonctionnalités similaires. Pour plus d’informations, consultez [Importer à partir de Power Pivot &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md).  
  
 Lorsque vous utilisez la fonctionnalité Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], gardez à l’esprit les points suivants :  
  
-   Pour utiliser la fonctionnalité Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], vous devez être connecté en tant que membre du rôle des Administrateurs du serveur sur l’instance Analysis Services.  
  
-   Le compte de service de l'instance Analysis Services doit avoir des autorisations de lecture sur le classeur à partir duquel vous effectuez la restauration.  
  
-   Par défaut, lorsque vous restaurez une base de données à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], la propriété Informations d’emprunt d’identité de source de données de la base de données model tabulaire a la valeur Par défaut, qui spécifie le compte de service de l’instance Analysis Services. Nous vous recommandons de modifier les informations d'identification d'emprunt d'identité vers un compte d'utilisateur Windows dans les Propriétés de la base de données. Pour plus d’informations, consultez [Emprunt d’identité &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
-   Les données du modèle de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sont copiées dans une base de données model tabulaire existante ou créée sur l’instance Analysis Services. Si votre classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contient des tables liées, elles seront recréées en tant que table sans source de données, similaire à une table créée à l’aide de l’option Coller dans une nouvelle table.  
  
### <a name="to-restore-from-power-pivot"></a>Pour restaurer à partir de PowerPivot  
  
1.  Dans SSMS, dans l’instance Active Directory vers laquelle vous souhaitez effectuer une restauration, cliquez avec le bouton droit sur **Bases de données**, puis cliquez sur **Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**.  
  
2.  Dans la boîte de dialogue **Restaurer à partir de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**, dans **Source de restauration**, dans **Fichier de sauvegarde**, cliquez sur **Parcourir**, puis sélectionnez un fichier .abf ou .xslx à partir duquel effectuer la restauration.  
  
3.  Dans **Destination de la restauration**, dans **Restaurer la base de données**, tapez un nom pour une nouvelle base de données ou une base de données existante. Si vous n'indiquez pas de nom, le nom du classeur est utilisé.  
  
4.  Dans **Emplacement de stockage**, cliquez sur **Parcourir**, puis sélectionnez un emplacement pour stocker la base de données.  
  
5.  Dans **Options**, conservez l'option **Inclure des informations sur la sécurité** activée. Lors d’une restauration à partir d’un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , ce paramètre ne s’applique pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de données model tabulaires #40;SSAS Tabulaire#41;](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)   
 [Importer à partir de Power Pivot &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)  
  
  
