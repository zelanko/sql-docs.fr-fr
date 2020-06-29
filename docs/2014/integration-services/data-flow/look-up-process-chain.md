---
title: Rechercher la chaîne de processus | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f6303ea4-fbbf-4cba-bc60-828df62be8c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eca04bf01440f323fbb0c430af025f8f17b95780
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85432096"
---
# <a name="look-up-process-chain"></a>Rechercher la chaîne de processus
  Utilisez la boîte de dialogue **Rechercher la chaîne de processus** pour rechercher une chaîne de processus qui est définie dans le système SAP Netweaver BW. Lorsque la liste de chaînes de processus disponibles apparaît, sélectionnez la chaîne de votre choix. La source remplira les options associées à l'aide des valeurs requises.  
  
 La source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW utilise la boîte de dialogue **Rechercher la chaîne de processus** . Pour en savoir plus sur la source SAP BW, consultez [SAP BW Source](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Rechercher la chaîne de processus**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source SAP BW.  
  
3.  Dans l' **Éditeur de source SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Dans la zone de groupe **Chaîne de processus** , cliquez sur **Rechercher** pour afficher la boîte de dialogue **Rechercher la chaîne de processus** .  
  
     La zone de groupe **Chaîne de processus** apparaît uniquement si la valeur de **Mode d’exécution** est **P - Déclencher une chaîne de processus**.  
  
## <a name="lookup-options"></a>Options de recherche  
 Dans les champs de recherche, vous pouvez filtrer les résultats à l'aide du caractère générique astérisque (*), ou en utilisant une chaîne partielle conjointement avec le caractère générique astérisque. Cependant, si vous laissez un champ de recherche vide, l'opération de recherche mettra uniquement en correspondance les chaînes vides de ce champ.  
  
 **Chaîne de processus**  
 Entrez le nom de la chaîne de processus à rechercher, ou entrez un nom partiel avec le caractère générique astérisque (*). Sinon, utilisez le caractère générique astérisque seul pour inclure toutes les chaînes de processus.  
  
 **Rechercher**  
 Recherchez des chaînes de processus correspondantes définies dans le système SAP Netweaver BW.  
  
## <a name="lookup-results"></a>Résultats de la recherche  
 Après avoir cliqué sur le bouton Rechercher, une liste de chaînes de processus dans le système SAP Netweaver BW apparaît dans un tableau avec les en-têtes de colonnes suivants :  
  
 **Chaîne de processus**  
 Affiche le nom de la chaîne de processus qui est définie dans le système SAP Netweaver BW.  
  
 **Description**  
 Affiche la description de la chaîne de processus.  
  
 Lorsque la liste de chaînes de processus disponibles apparaît, sélectionnez la chaîne de votre choix. La source remplira les options associées à l'aide des valeurs requises.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source SAP BW &#40;page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
