---
title: Options (éditeur de texte-XML-page mise en forme) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: f96625c9658c3bd9864f0928e738357b6e14311e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66089844"
---
# <a name="options-text-editor---xml---formatting-page"></a>Options (Éditeur de texte - XML - Page Mise en forme)

Cette boîte de dialogue vous permet de spécifier les paramètres de mise en forme de l'Éditeur XML. Vous pouvez accéder à la boîte de dialogue **Options** à partir du menu **Outils**.  
  
> [!NOTE]  
> Ces paramètres sont disponibles lorsque vous sélectionnez le dossier **Éditeur de texte**, le dossier **XML**, puis l’option **Mise en forme** de la boîte de dialogue **Options**.  
  
## <a name="attributes"></a>Attributs  
 **Préserver la mise en forme manuelle des attributs**  
 Indique qu'il ne faut pas remettre en forme les attributs. Il s’agit de la valeur par défaut.  
  
> [!NOTE]  
>  Si les attributs se trouvent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs de façon à correspondre à la mise en retrait de l'élément parent.  
  
 **Aligner les attributs chacun sur une ligne séparée **  
 Aligne verticalement le deuxième attribut et les attributs suivants de façon à correspondre à la mise en retrait du premier attribut. Le texte XML suivant montre comment les attributs sont alignés lorsque cette option est sélectionnée.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a>Remise en forme automatique  
 **En collant le contenu du presse-papiers **  
 Remet en forme le texte XML collé à partir du Presse-papiers.  
  
 **Après la balise de fin **  
 Remet en forme l'élément lorsque la balise de fin est insérée.  
  
## <a name="mixed-content"></a>Contenu mixte  
 **Formater les contenus mixtes par défaut **  
 Tente de remettre en forme le contenu mixte, sauf lorsque celui-ci se trouve dans une étendue `xml:space="preserve"`. Il s’agit de la valeur par défaut.  
  
 Si un élément contient un mélange de texte et de balises, le contenu est considéré comme mixte. Voici un exemple de contenu mixte.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \<>/dir  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md)  
