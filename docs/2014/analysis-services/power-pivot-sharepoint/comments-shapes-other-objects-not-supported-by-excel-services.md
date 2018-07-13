---
title: 'Les fonctionnalités suivantes ne sont pas pris en charge par Excel Services et ne peut pas afficher ou peut afficher que partiellement : commentaires, les formes ou autres objets | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1bee0273ba256ea6861b4259d48e377528c5e4eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192417"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a>Les fonctionnalités suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s'afficher ou de ne s'afficher que partiellement : les commentaires, les formes ou d'autres objets
  Cette erreur se produit lorsque vous ajoutez des segments à un classeur PowerPivot à partir d'une liste de champs PowerPivot.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|Excel Web Access ne peut pas restituer l'objet Forme utilisé pour contrôler le positionnement et la mise en forme des segments ajoutés à un classeur à partir de la liste de champs PowerPivot.|  
|Texte du message|Les fonctionnalités suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s'afficher ou de ne s'afficher que partiellement :<br /><br /> les commentaires, les formes ou d'autres objets<br /><br /> Certaines fonctionnalités, comme les requêtes de données externes, affichent des données mises en cache qui ne peuvent être actualisées que dans Microsoft Excel.|  
  
## <a name="explanation"></a>Explication  
 Excel Web Access affiche cette erreur lorsque vous ouvrez un classeur PowerPivot dans un navigateur et que vous cliquez sur le **détails** bouton pour le message, **non pris en charge cette fonctionnalités classeur ne peut pas s’affiche comme prévu**.  
  
 Cette erreur se produit parce que le classeur PowerPivot contient des segments dont la disposition est contrôlée par un objet Forme masqué dans Excel. L'objet Forme contrôle la mise en forme et le positionnement des segments dans les placements horizontaux et verticaux.  
  
 Excel Services ne peut pas restituer un objet Forme, mais étant donné que l'objet est masqué, le fait qu'il n'effectue le rendu n'est pas un problème.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cette erreur peut être ignorée. Cliquez sur **OK** pour fermer le message d'erreur et utiliser le classeur et les segments sans problème.  
  
  
