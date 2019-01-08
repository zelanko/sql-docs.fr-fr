---
title: Définir les propriétés d’un composant de flux de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], properties
ms.assetid: 73000ef6-52a2-4dec-8320-0e79acf0c2c5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9ac3714dbbd96150aa9d670e370e8a475f6a57e1
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52817951"
---
# <a name="set-the-properties-of-a-data-flow-component"></a>Définir les propriétés d’un composant de flux de données
  Pour définir les propriétés de composants de flux de données, qui incluent des sources, des destinations et des transformations, utilisez l'une des fonctionnalités suivantes :  
  
-   Les éditeurs de composants fournis par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Ces éditeurs ne peuvent être utilisés que pour définir les propriétés personnalisées de chaque composant de flux de données.  
  
-   La fenêtre **Propriétés** énumère les propriétés personnalisées définies au niveau du composant pour chaque élément, ainsi que les propriétés communes à tous les éléments du flux de données.  
  
-   La boîte de dialogue **Éditeur avancé** permet d’accéder aux propriétés personnalisées pour chaque composant. La boîte de dialogue **Éditeur avancé** permet aussi d’accéder aux propriétés communes à l’ensemble des composants de flux de données, à savoir les propriétés des entrées, des sorties, des sorties d’erreurs, des colonnes et des colonnes externes.  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-a-component-editor"></a>Pour définir les propriétés d'un composant de flux de données à l'aide d'un éditeur de composant  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données qui contient le flux de données et le composant dont vous voulez afficher ou modifier les propriétés.  
  
4.  Double-cliquez sur le composant du flux de données.  
  
5.  Dans l'éditeur de composant, affichez ou modifiez les valeurs des propriétés, puis fermez l'éditeur.  
  
6.  Pour enregistrer le package mis à jour, dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés**.  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-properties-window"></a>Pour définir les propriétés d'un composant de flux de données à l'aide de la fenêtre Propriétés  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données qui contient le composant dont vous voulez afficher ou modifier les propriétés.  
  
4.  Cliquez avec le bouton droit sur le composant du flux de données, puis cliquez sur **Propriétés**.  
  
5.  Affichez ou modifiez les valeurs des propriétés, puis fermez la fenêtre **Propriétés** .  
  
    > [!NOTE]  
    >  De nombreuses propriétés sont en lecture seule et ne peuvent donc pas être modifiées.  
  
6.  Pour enregistrer le package mis à jour, dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés**.  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-advanced-editor"></a>Pour définir les propriétés d'un composant de flux de données à l'aide de l'éditeur avancé  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données qui contient le composant à afficher ou à modifier.  
  
4.  Dans le concepteur de flux de données, cliquez avec le bouton droit sur le composant du flux de données, puis cliquez sur **Afficher l’éditeur avancé**.  
  
    > [!NOTE]  
    >  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les composants de flux de données qui prennent en charge plusieurs entrées ne peuvent pas utiliser **l’éditeur avancé**.  
  
5.  Dans la boîte de dialogue **Éditeur avancé** , procédez de l’une des façons suivantes :  
  
    -   Pour afficher et spécifier la connexion utilisée par le composant, cliquez sur l’onglet **Gestionnaires de connexions** .  
  
        > [!NOTE]  
        >  L’onglet **Gestionnaire de connexions** est accessible uniquement aux composants de flux de données qui utilisent des gestionnaires de connexions pour se connecter à des sources de données telles que des fichiers et des bases de données.  
  
    -   Pour afficher et modifier les propriétés au niveau du composant, cliquez sur l’onglet **Propriétés du composant** .  
  
    -   Pour afficher et modifier les mappages entre des colonnes externes et la sortie disponible, cliquez sur l’onglet **Mappage de colonnes** .  
  
        > [!NOTE]  
        >  L’onglet **Mappage de colonnes** est disponible uniquement pendant l’affichage ou la modification des sources et des destinations.  
  
    -   Pour afficher la liste des colonnes d’entrée disponibles et mettre à jour le nom des colonnes de sortie, cliquez sur l’onglet **Colonnes d’entrée** .  
  
        > [!NOTE]  
        >  L'onglet Colonnes d'entrée est disponible uniquement en cas d'utilisation de transformations ou de destinations. Pour plus d’informations, consultez [Transformations Integration Services](transformations/integration-services-transformations.md).  
  
    -   Pour afficher et modifier les propriétés des entrées, des sorties, des sorties d’erreur et les propriétés des colonnes qu’elles contiennent, cliquez sur l’onglet **Propriétés d’entrée et de sortie** .  
  
        > [!NOTE]  
        >  Les sources ne comportent pas d'entrées. Les destinations ne comportent pas de sorties, sauf pour une sortie d'erreur facultative.  
  
6.  Affichez ou modifiez les valeurs des propriétés.  
  
7.  Cliquez sur **OK**.  
  
8.  Pour enregistrer le package mis à jour, dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Transformations Integration Services](transformations/integration-services-transformations.md)  
  
  
