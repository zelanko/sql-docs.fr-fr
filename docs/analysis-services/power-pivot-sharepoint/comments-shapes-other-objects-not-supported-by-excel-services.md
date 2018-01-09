---
title: Commentaires, les formes, les autres objets non pris en charge par Excel Services | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e81433f28d9b3b3f20ceb99f2e6436a689ba4e86
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="comments-shapes-other-objects-not-supported-by-excel-services"></a>Commentaires, les formes, les autres objets non pris en charge par Excel Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Cette erreur se produit lorsque vous ajoutez des segments à un [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] classeur à partir d’un [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] liste de champs.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|Excel Web Access ne peut pas restituer l’objet Forme utilisé pour contrôler le positionnement et la mise en forme des segments ajoutés à un classeur à partir de la liste de champs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
|Texte du message|Les fonctionnalités suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s'afficher ou de ne s'afficher que partiellement :<br /><br /> les commentaires, les formes ou d'autres objets<br /><br /> Certaines fonctionnalités, comme les requêtes de données externes, affichent des données mises en cache qui ne peuvent être actualisées que dans Microsoft Excel.|  
  
## <a name="explanation"></a>Explication  
 Excel Web Access affiche cette erreur lorsque vous ouvrez un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans un navigateur et que vous cliquez sur le bouton **Détails** du message **Fonctionnalités non prises en charge. Il se peut que votre classeur ne s’affiche pas comme vous le souhaitez**.  
  
 Cette erreur se produit parce que le classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contient des segments dont la disposition est contrôlée par un objet Forme masqué dans Excel. L'objet Forme contrôle la mise en forme et le positionnement des segments dans les placements horizontaux et verticaux.  
  
 Excel Services ne peut pas restituer un objet Forme, mais étant donné que l'objet est masqué, le fait qu'il n'effectue le rendu n'est pas un problème.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cette erreur peut être ignorée. Cliquez sur **OK** pour fermer le message d'erreur et utiliser le classeur et les segments sans problème.  
  
  
