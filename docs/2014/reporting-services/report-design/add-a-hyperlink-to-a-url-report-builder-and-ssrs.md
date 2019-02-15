---
title: Ajouter un lien hypertexte à une URL (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d3392c0b-7b62-4d27-bc04-2bd0c5487d08
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a40980ddd8ee29d05fe4278baf512790751ee7d8
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56293785"
---
# <a name="add-a-hyperlink-to-a-url-report-builder-and-ssrs"></a>Ajouter un lien hypertexte à une URL (Générateur de rapports et SSRS)
  Vous pouvez ajouter un lien hypertexte à un élément de rapport lorsque vous souhaitez que les utilisateurs soient en mesure de cliquer sur un lien dans un rapport et d'ouvrir un navigateur vers l'URL que vous spécifiez. Un lien hypertexte peut être une URL statique ou une expression qui est évaluée en une URL. Si une base de données comprend un champ avec des URL, vous pouvez insérer ce champ dans l'expression de façon à produire une liste dynamique de liens hypertexte dans le rapport. Vous pouvez ajouter des liens hypertexte aux zones de texte, aux images, aux graphiques et aux jauges. Vous devez vous assurer que l'utilisateur a accès à l'URL que vous fournissez.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Vous pouvez également spécifier des URL vers des rapports sur n'importe quel serveur de rapports que vos utilisateurs et vous-même avez l'autorisation d'afficher en utilisant des demandes d'URL dirigées vers le serveur de rapports. Par exemple, vous pouvez spécifier un rapport et masquer l'explorateur de documents à l'utilisateur lorsqu'il affiche pour la première fois le rapport. Pour plus d’informations, consultez [Accès URL &#40;SSRS&#41;](../url-access-ssrs.md) dans la [documentation de Reporting Services](https://go.microsoft.com/fwlink/?linkid=121312) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vous pouvez ajouter un lien hypertexte à une URL vers tout élément qui a une propriété **Action** , par exemple une zone de texte, une image ou une série calculée dans un graphique. Lorsque l'utilisateur clique sur l'élément de rapport en question, l'action que vous définissez est exécutée. Pour plus d’informations, consultez [Boîte de dialogue Propriétés relatives aux actions &#40;Générateur de rapports et SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) et [Spécification de chemins d’accès à des éléments externes &#40;Générateur de rapports et SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
 Pour démarrer rapidement, consultez [Tutoriel : Mettre en forme du texte &#40;Générateur de rapports&#41;](../tutorial-format-text-report-builder.md).  
  
> [!NOTE]  
>  Les liens qui sont associés à des champs de dataset peuvent être vulnérables à des opérations de falsification à des fins malveillantes. Pour plus d’informations, consultez [Sécuriser des rapports et des ressources](../security/secure-reports-and-resources.md) dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][documentation en ligne](https://go.microsoft.com/fwlink/?LinkId=154888) sur msdn.microsoft.com.  
  
### <a name="to-add-a-hyperlink"></a>Pour ajouter un lien hypertexte  
  
1.  En mode création de rapport, cliquez avec le bouton droit sur la zone de texte, l'image ou le graphique auquel vous voulez ajouter un lien, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue Propriétés, cliquez sur **Action**.  
  
3.  Sélectionnez **Atteindre l'URL**. Une section supplémentaire apparaît dans la boîte de dialogue pour cette option.  
  
4.  Dans **Sélectionner une URL**, tapez ou sélectionnez une URL ou une expression qui prend la valeur d'une URL ou cliquez sur la flèche déroulante et cliquez sur le nom d'un champ qui contient une URL.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  (Facultatif) Le texte n'est pas mis en forme automatiquement en tant que lien. Pour le texte, il est utile de modifier la couleur et l'effet du texte pour indiquer qu'il s'agit d'un lien. Par exemple, changez la couleur en bleu et l'effet en soulignement dans la section **Police** sous l'onglet Accueil du ruban.  
  
7.  Pour tester le lien, cliquez sur **Exécuter** afin d'afficher l'aperçu du rapport, puis cliquez sur l'élément de rapport sur lequel vous avez défini ce lien.  
  
## <a name="see-also"></a>Voir aussi  
 [Tri interactif, Explorateurs de documents et liens &#40;Générateur de rapports et SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)   
 [Créer un explorateur de documents &#40;Générateur de rapports et SSRS&#41;](create-a-document-map-report-builder-and-ssrs.md)  
  
  
