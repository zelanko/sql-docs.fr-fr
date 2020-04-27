---
title: Collections intégrées dans les expressions (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 78d5e3b8-9320-4e4b-a025-e2de3cf7afa7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e572e6bd7070247c8e872283964f50ad734d4e32
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106417"
---
# <a name="built-in-collections-in-expressions-report-builder-and-ssrs"></a>Collections intégrées dans les expressions (Générateur de rapports et SSRS)
  Dans une expression d'un rapport, vous avez la possibilité d'inclure des références aux collections intégrées suivantes : ReportItems, Parameters, Fields, DataSets, DataSources, Variables, ainsi que des champs prédéfinis pour les informations globales telles que le nom du rapport. Les collections ne sont pas toutes répertoriées dans la boîte de dialogue **Expression** . En effet, les collections DataSets et DataSources ne sont disponibles qu'au moment de l'exécution pour les rapports publiés sur un serveur de rapports. La collection ReportItems représente l'ensemble des zones de texte figurant dans une partie du rapport, comme celles qui sont situées dans une page ou dans un en-tête de page.  
  
 Pour plus d’informations, consultez [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="understanding-built-in-collections"></a><a name="Collections"></a> Fonctionnement des collections intégrées  
 Le tableau suivant répertorie les collections intégrées disponibles lorsque vous écrivez une expression. Chaque ligne inclut le nom de programmation, sensible à la casse, de la collection, indique si vous pouvez utiliser la boîte de dialogue Expression pour ajouter une référence à la collection de manière interactive, propose un exemple et précise quand les valeurs de la collection sont initialisées et peuvent être utilisées.  
  
|Collection intégrée|Catégorie dans la boîte de dialogue Expression|Exemple|Description|  
|--------------------------|-------------------------------------------|-------------|-----------------|  
|`Globals`|Champs prédéfinis|`=Globals.ReportName`<br /><br /> `- or -`<br /><br /> `=Globals.PageNumber`|Représente les variables globales utilisables pour des rapports, par exemple le nom du rapport ou le numéro de page. Toujours disponible.<br /><br /> Pour plus d’informations, consultez [Références à des champs Globals et Users prédéfinis &#40;Générateur de rapports et SSRS&#41;](built-in-collections-built-in-globals-and-users-references-report-builder.md).|  
|`User`|Champs prédéfinis|`=User.UserID`<br /><br /> - ou -<br /><br /> `=User.Language`|Représente une collection de données sur l'utilisateur exécutant le rapport, par exemple le paramètre de langue ou l'ID utilisateur. Toujours disponible.<br /><br /> Pour plus d’informations, consultez [Références à des champs Globals et Users prédéfinis &#40;Générateur de rapports et SSRS&#41;](built-in-collections-built-in-globals-and-users-references-report-builder.md).|  
|`Parameters`|Paramètres|`=Parameters("ReportMonth").Value`<br /><br /> - ou -<br /><br /> `=Parameters!ReportYear.Value`|Représente la collection des paramètres de rapport, chacun pouvant correspondre à une valeur unique ou à plusieurs valeurs. Non disponible tant que l'initialisation du traitement n'est pas terminée. Pour plus d’informations, consultez [Informations de référence sur la collection de paramètres &#40;Générateur de rapports et SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md).|  
|`Fields(`* \<DataSet>*`)`|Champs|`=Fields!Sales.Value`|Représente la collection des champs du dataset qui sont disponibles pour le rapport. Disponibles après extraction des données d'une source de données dans un dataset. Pour plus d’informations, consultez [Référence à une collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md).|  
|`DataSets`|Non affichée|`=DataSets("TopEmployees").CommandText`|Représente la collection de sources de données référencées à partir du corps d'une définition de rapport. N'inclut pas les sources de données utilisées uniquement dans les en-têtes ou les pieds de page. Non disponible dans l'aperçu local. Pour plus d’informations, consultez [Références à des collections DataSources et DataSets &#40;Générateur de rapports et SSRS&#41;](built-in-collections-datasources-and-datasets-references-report-builder.md).|  
|`DataSources`|Non affichée|`=DataSources("AdventureWorks2012").Type`|Représente la collection des sources de données référencées à partir du corps d'un rapport. N'inclut pas les sources de données utilisées uniquement dans les en-têtes ou les pieds de page. Non disponible dans l'aperçu local. Pour plus d’informations, consultez [Références à des collections DataSources et DataSets &#40;Générateur de rapports et SSRS&#41;](built-in-collections-datasources-and-datasets-references-report-builder.md).|  
|`Variables`|`Variables`|`=Variables!CustomTimeStamp.Value`|Représente la collection des variables de rapport et de groupe. Pour plus d’informations, consultez [Références à des collections de variables de rapport et de groupe &#40;Générateur de rapports et SSRS&#41;](built-in-collections-report-and-group-variables-references-report-builder.md).|  
|`ReportItems`|Non affichée|`=ReportItems("Textbox1").Value`|Représente la collection des zones de texte d'un élément de rapport. Cette collection peut être utilisée pour proposer un résumé des éléments présents dans la page en vue de leur inclusion dans un en-tête ou un pied de page. Pour plus d’informations, consultez [Références à la collection ReportItems &#40;Générateur de rapports et SSRS&#41;](built-in-collections-reportitems-collection-references-report-builder.md).|  
  
##  <a name="using-collection-syntax-in-an-expression"></a><a name="Syntax"></a> Utilisation de la syntaxe de collection dans une expression  
 Pour faire référence à une collection à partir d’une expression [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , utilisez la syntaxe standard pour un élément dans une collection. Le tableau ci-après propose des exemples de syntaxe de collection.  
  
|Syntaxe|Exemple|  
|------------|-------------|  
|*Collecte! ObjectName. Property*|`=Fields!Sales.Value`|  
|*Collecte! ObjectName ("propriété")*|`=Fields!Sales("Value")`|  
|*Collection("NomObjet").Propriété*|`=Fields("Sales").Value`|  
|*Collection("Membre")*|`=User("Language")`|  
|*Collection. Member*|`=User.Language`|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter une expression &#40;Générateur de rapports et SSRS&#41;](add-an-expression-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)  
  
  
