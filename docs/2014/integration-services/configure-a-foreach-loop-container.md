---
title: Configurer un conteneur de boucles Foreach | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Foreach Loop containers
- containers [Integration Services], Foreach Loop
ms.assetid: 519c6f96-5e1f-47d2-b96a-d49946948c25
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 840011d1797c7ef9482af31ffc8b3ec3a6419b8a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84921970"
---
# <a name="configure-a-foreach-loop-container"></a>Configurer un conteneur de boucles Foreach
  Cette procédure décrit comment configurer un conteneur de boucles Foreach, notamment les expressions de la propriété au niveau de l'énumérateur et du conteneur.  
  
### <a name="to-configure-the-foreach-loop-container"></a>Pour configurer le conteneur de boucles Foreach  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la boucle Foreach.  
  
3.  Dans la boîte de dialogue **Éditeur de boucle Foreach** , cliquez sur **Général** et, si vous le souhaitez, modifiez le nom et la description de la boucle Foreach.  
  
4.  Cliquez sur **Collection** , puis sélectionnez un type d’énumérateur dans la liste **Énumérateur** .  
  
5.  Indiquez un énumérateur et définissez ses options de la manière suivante :  
  
    -   Pour utiliser l’énumérateur Foreach File, indiquez le dossier contenant les fichiers à énumérer, spécifiez un filtre pour le nom et le type de fichier, et indiquez si le nom de fichier complet doit être retourné. Indiquez enfin si les fichiers des sous-dossiers doivent également être énumérés.  
  
    -   Pour utiliser l’énumérateur Foreach Item, cliquez sur **Colonnes**et, dans la boîte de dialogue **Colonnes For Each Item** , cliquez sur **Ajouter** pour ajouter des colonnes. Sélectionnez un type de données dans la liste **Type de données** pour chaque colonne, puis cliquez sur **OK**.  
  
         Tapez des valeurs dans les colonnes ou sélectionnez des valeurs dans les listes.  
  
        > [!NOTE]  
        >  Pour ajouter une nouvelle ligne, cliquez n'importe où en dehors de la cellule dans laquelle vous avez tapé une valeur.  
  
        > [!NOTE]  
        >  Si une valeur n'est pas compatible avec le type de données de la colonne, le texte est mis en surbrillance.  
  
    -   Pour utiliser l’énumérateur ADO Foreach, sélectionnez une variable existante ou cliquez sur **Nouvelle variable** dans la liste **Variable source de l’objet ADO** pour spécifier la variable contenant le nom de l’objet ADO à énumérer et sélectionnez une option de mode d’énumération.  
  
         Si vous créez une variable, définissez ses propriétés dans la boîte de dialogue **Ajouter une variable** .  
  
    -   Pour utiliser l’énumérateur d’ensemble de lignes du schéma ADO.NET Foreach, sélectionnez une connexion ADO.NET existante ou cliquez sur **Nouvelle connexion** dans la liste **Connexion** , puis sélectionnez un schéma.  
  
         Si vous le souhaitez, cliquez sur **Définir les restrictions** et sélectionnez des restrictions de schéma, sélectionnez la variable qui contient la valeur de restriction ou tapez cette valeur, puis cliquez sur **OK**.  
  
    -   Pour utiliser l’énumérateur Foreach à partir d’une variable, sélectionnez une variable dans la liste **Variable** .  
  
    -   Pour utiliser l’énumérateur Foreach NodeList, cliquez sur DocumentSourceType et sélectionnez le type de source dans la liste, puis cliquez sur DocumentSource. En fonction de la valeur sélectionnée pour DocumentSourceType, sélectionnez une variable ou une connexion de fichier dans la liste, créez une variable ou une connexion de fichier, ou tapez la source XML dans **l’Éditeur de source de document**.  
  
         Cliquez ensuite sur EnumerationType et sélectionnez un type d’énumération dans la liste. Si la valeur pour EnumerationType est **Navigator, Node ou NodeText**, cliquez sur OuterXPathStringSourceType et sélectionnez le type de source, puis cliquez sur OuterXPathStringSourceType. En fonction de la valeur définie pour OuterXPathStringSourceType, sélectionnez une variable ou une connexion de fichier dans la liste, créez une variable ou une connexion de fichier, ou tapez la chaîne de l’expression XPath (XML Path Language) externe.  
  
         Si la valeur pour EnumerationType est **ElementCollection**, définissez OuterXPathStringSourceType et OuterXPathString conformément aux instructions ci-dessus. Cliquez ensuite sur InnerElementType, sélectionnez un type d’énumération pour les éléments internes, puis cliquez sur InnerXPathStringSourceType. En fonction de la valeur définie pour InnerXPathStringSourceType, sélectionnez une variable ou une connexion de fichier, créez une variable ou une connexion de fichier, ou tapez la chaîne de l’expression XPath interne.  
  
    -   Pour utiliser l’énumérateur SMO Foreach, sélectionnez une connexion ADO.NET existante ou cliquez sur **Nouvelle connexion** dans la liste **Connexion** , puis tapez la chaîne à utiliser ou cliquez sur **Parcourir**. Si vous cliquez sur **Parcourir**, dans la boîte de dialogue **Sélectionner l’énumération SMO** , sélectionnez le type d’objet à énumérer et le type d’énumération, puis cliquez sur **OK**.  
  
6.  Si vous le souhaitez, cliquez sur le bouton Parcourir **(...)** dans la zone de texte **expressions** de la page **collection** pour créer des expressions qui mettent à jour des valeurs de propriété. Pour plus d’informations, consultez [Ajouter ou modifier une Expression de propriété](expressions/add-or-change-a-property-expression.md).  
  
    > [!NOTE]  
    >  Les propriétés énumérées dans la liste **Propriété** varient en fonction de l’énumérateur.  
  
7.  Si vous le souhaitez, cliquez sur **Mappage de variables** pour mapper des propriétés d’objets à la valeur de la collection, puis procédez comme suit :  
  
    1.  Dans la liste **variables** , sélectionnez une variable ou cliquez sur **\<New Variable>** pour en créer une.  
  
    2.  Si vous ajoutez une nouvelle variable, définissez ses propriétés dans la boîte de dialogue **Ajouter une variable** et cliquez sur **OK**.  
  
    3.  Si vous utilisez l’énumérateur Foreach Item, vous pouvez mettre à jour la valeur de l’index dans la liste **Index** .  
  
        > [!NOTE]  
        >  La valeur de l'index indique quelle colonne de l'élément mapper à la variable. Seul l'énumérateur For Each Item peut utiliser une valeur d'index autre que 0.  
  
8.  Si vous le souhaitez, cliquez sur **Expressions** et, dans la page **Expressions** , créez des expressions de propriété pour les propriétés du conteneur de boucles Foreach. Pour plus d’informations, consultez [Ajouter ou modifier une Expression de propriété](expressions/add-or-change-a-property-expression.md).  
  
9. Cliquez sur **OK**.  
  
## <a name="see-also"></a> Voir aussi  
 [Conteneur de boucles Foreach](control-flow/foreach-loop-container.md)  
  
  
