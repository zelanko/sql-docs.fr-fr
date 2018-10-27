---
title: Document and Script an Analysis Services Database | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML for Analysis, scripts
- XMLA, scripts
- scripts [Analysis Services], databases
- documenting databases
- databases [Analysis Services], documenting
- databases [Analysis Services], scripts
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a1a10d27612d127bcc9fcc5ca60f97575f6fc1fe
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144686"
---
# <a name="document-and-script-an-analysis-services-database"></a>Documenter et générer des scripts pour une base de données Analysis Services
  Après le déploiement d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour sortir les métadonnées de la base de données ou d’un objet contenu dans la base de données, comme un script XMLA (XML for Analysis). Vous pouvez sortir ce script dans une nouvelle fenêtre **Éditeur de requête XMLA** , dans un fichier ou dans le Presse-papiers. Pour plus d’informations, consultez [Analysis Services Scripting Language &#40;ASSL&#41; référence](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).  
  
 Le script XMLA généré utilise des éléments ASSL ( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language) pour définir les objets contenus dans le script. Si vous avez généré un script CREATE, le script XMLA obtenu contient une commande XMLA **CREATE** et des éléments ASSL qui peuvent être utilisés pour créer l’intégralité de la structure de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur une instance. Si vous avez généré un script ALTER, le script XMLA obtenu contient une commande XMLA **ALTER** et des éléments ASSL qui peuvent être utilisés pour restaurer la structure d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existante dans l’état où la base de données se trouvait au moment de la génération du script.  
  
 Vous pouvez utiliser le script XMLA généré à partir d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de nombreuses manières, par exemple :  
  
-   pour maintenir un script de sauvegarde qui vous permet de recréer tous les objets et toutes les autorisations de la base de données ;  
  
-   pour créer ou mettre à jour le code de développement de la base de données ;  
  
-   pour créer un environnement de test ou de développement à partir d'un schéma existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier ou supprimer une base de données Analysis Services](modify-or-delete-an-analysis-services-database.md)   
 [Élément Alter &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)   
 [Élément Create &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)  
  
  
