---
title: Commentaires, les formes, les autres objets non pris en charge par Excel Services | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d7ceef898de9e82c46a2d058f8c35d9b2d1ef7ec
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="comments-shapes-other-objects-not-supported-by-excel-services"></a>Commentaires, les formes, les autres objets non pris en charge par Excel Services
  Cette erreur se produit lorsque vous ajoutez des segments à un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] à partir d’une liste de champs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
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
  
  
