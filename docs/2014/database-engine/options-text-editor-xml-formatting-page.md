---
title: Options (Page de mise en forme de l’éditeur de texte - XML -) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5d77f7351d712f63e9cfc92c3ff03b131cb6d5d3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040027"
---
# <a name="options-text-editor---xml---formatting-page"></a>Options (Éditeur de texte - XML - Page Mise en forme)
  Cette boîte de dialogue vous permet de spécifier les paramètres de mise en forme de l'Éditeur XML. Vous pouvez accéder à la boîte de dialogue **Options** à partir du menu **Outils**.  
  
> [!NOTE]  
>  Ces paramètres sont disponibles lorsque vous sélectionnez le dossier **Éditeur de texte**, le dossier **XML**, puis l’option **Mise en forme** de la boîte de dialogue **Options**.  
  
## <a name="attributes"></a>Attributs  
 **Conserver la mise en forme manuelle des attributs**  
 Indique qu'il ne faut pas remettre en forme les attributs. Il s'agit du paramètre par défaut.  
  
> [!NOTE]  
>  Si les attributs se trouvent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs de façon à correspondre à la mise en retrait de l'élément parent.  
  
 **Aligner les attributs chacun sur une ligne distincte**  
 Aligne verticalement le deuxième attribut et les attributs suivants de façon à correspondre à la mise en retrait du premier attribut. Le texte XML suivant montre comment les attributs sont alignés lorsque cette option est sélectionnée.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a>Remise en forme automatique  
 **Lors du collage à partir du Presse-papiers.**  
 Remet en forme le texte XML collé à partir du Presse-papiers.  
  
 **À la fin de la balise de fin**  
 Remet en forme l'élément lorsque la balise de fin est insérée.  
  
## <a name="mixed-content"></a>Contenu mixte  
 **Formater les contenus mixtes par défaut.**  
 Tente de remettre en forme le contenu mixte, sauf lorsque celui-ci se trouve dans une étendue `xml:space="preserve"`. Il s'agit du paramètre par défaut.  
  
 Si un élément contient un mélange de texte et de balises, le contenu est considéré comme mixte. Voici un exemple de contenu mixte.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \<dir >  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)  
  
  