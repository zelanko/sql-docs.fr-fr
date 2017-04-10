---
title: "Les fonctionnalit&#233;s suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s&#39;afficher ou de ne s&#39;afficher que partiellement : les commentaires, les formes ou d&#39;autres objets | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 6
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Les fonctionnalit&#233;s suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s&#39;afficher ou de ne s&#39;afficher que partiellement : les commentaires, les formes ou d&#39;autres objets
  Cette erreur se produit lorsque vous ajoutez des segments à un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] à partir d’une liste de champs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## Détails  
  
|||  
|-|-|  
|S'applique à|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|Excel Web Access ne peut pas restituer l’objet Forme utilisé pour contrôler le positionnement et la mise en forme des segments ajoutés à un classeur à partir de la liste de champs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
|Texte du message|Les fonctionnalités suivantes ne sont pas prises en charge par Excel Services et risquent de ne pas s'afficher ou de ne s'afficher que partiellement :<br /><br /> les commentaires, les formes ou d'autres objets<br /><br /> Certaines fonctionnalités, comme les requêtes de données externes, affichent des données mises en cache qui ne peuvent être actualisées que dans Microsoft Excel.|  
  
## Explication  
 Excel Web Access affiche cette erreur lorsque vous ouvrez un classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans un navigateur et que vous cliquez sur le bouton **Détails** du message **Fonctionnalités non prises en charge. Il se peut que votre classeur ne s’affiche pas comme vous le souhaitez**.  
  
 Cette erreur se produit parce que le classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contient des segments dont la disposition est contrôlée par un objet Forme masqué dans Excel. L'objet Forme contrôle la mise en forme et le positionnement des segments dans les placements horizontaux et verticaux.  
  
 Excel Services ne peut pas restituer un objet Forme, mais étant donné que l'objet est masqué, le fait qu'il n'effectue le rendu n'est pas un problème.  
  
## Action de l'utilisateur  
 Cette erreur peut être ignorée. Cliquez sur **OK** pour fermer le message d'erreur et utiliser le classeur et les segments sans problème.  
  
  