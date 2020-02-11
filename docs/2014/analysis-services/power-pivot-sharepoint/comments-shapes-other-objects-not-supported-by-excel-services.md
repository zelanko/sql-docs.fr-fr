---
title: 'Les fonctionnalités suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s’afficher ou de ne s’afficher que partiellement : les commentaires, les formes ou d’autres objets | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 03411134eb1350adcd37badd458e7f7a0198a9ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071919"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a>Les fonctionnalités suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s'afficher ou de ne s'afficher que partiellement : les commentaires, les formes ou d'autres objets
  Cette erreur se produit lorsque vous ajoutez des segments à un classeur PowerPivot à partir d'une liste de champs PowerPivot.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S’applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause :|Excel Web Access ne peut pas restituer l'objet Forme utilisé pour contrôler le positionnement et la mise en forme des segments ajoutés à un classeur à partir de la liste de champs PowerPivot.|  
|Texte du message|Les fonctionnalités suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s'afficher ou de ne s'afficher que partiellement :<br /><br /> les commentaires, les formes ou d'autres objets<br /><br /> Certaines fonctionnalités, comme les requêtes de données externes, affichent des données mises en cache qui ne peuvent être actualisées que dans Microsoft Excel.|  
  
## <a name="explanation"></a>Explication  
 Excel Accès web affiche cette erreur lorsque vous ouvrez un classeur PowerPivot dans un navigateur et que vous cliquez sur le bouton **Détails** du message, **fonctionnalités non prises en charge que ce classeur risque de ne pas afficher comme prévu**.  
  
 Cette erreur se produit parce que le classeur PowerPivot contient des segments dont la disposition est contrôlée par un objet Forme masqué dans Excel. L'objet Forme contrôle la mise en forme et le positionnement des segments dans les placements horizontaux et verticaux.  
  
 Excel Services ne peut pas restituer un objet Forme, mais étant donné que l'objet est masqué, le fait qu'il n'effectue le rendu n'est pas un problème.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cette erreur peut être ignorée. Cliquez sur **OK** pour fermer le message d'erreur et utiliser le classeur et les segments sans problème.  
  
  
