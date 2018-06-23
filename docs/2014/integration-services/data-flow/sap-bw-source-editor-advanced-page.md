---
title: Éditeur de source SAP BW (page Avancé) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44f3c991-9e8f-4126-a9a2-2d9da779fb11
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9d341b6c2320dfe5a7cc3645396434fa46b0779c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041163"
---
# <a name="sap-bw-source-editor-advanced-page"></a>Éditeur de source SAP BW (page Avancé)
  Utilisez la page **Avancé** de **l’Éditeur de source SAP BW** pour spécifier la règle de conversion de chaînes et le délai d’attente, et également pour réinitialiser l’état d’un ID de demande particulier.  
  
 Pour en savoir plus sur le composant source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [Source SAP BW](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
 **Pour ouvrir la page Gestionnaire de connexions**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source SAP BW.  
  
3.  Dans **l’Éditeur de source SAP BW**, cliquez sur **Avancé** pour ouvrir la page **Avancé** de l’éditeur.  
  
## <a name="options"></a>Options  
  
> [!NOTE]  
>  Si vous ne connaissez pas toutes les valeurs requises pour configurer la source, adressez-vous à votre administrateur SAP.  
  
 **Conversion de chaîne**  
 Spécifiez la règle à appliquer pour la conversion de chaîne.  
  
|Option|Description|  
|------------|-----------------|  
|**Conversion de chaîne automatique**|Convertir toutes les chaînes en `nvarchar` lorsque le système SAP Netweaver BW est un système Unicode. Sinon, convertissez toutes les chaînes en `varchar`.|  
|**Convertir les chaînes en varchar**|Convertissez toutes les chaînes en `varchar`.|  
|**Convertir les chaînes en nvarchar**|Convertissez toutes les chaînes en `nvarchar`.|  
  
 **Délai d'attente (secondes)**  
 Spécifiez le nombre maximal de secondes pendant lesquelles la source doit attendre.  
  
> [!NOTE]  
>  Cette option n’est valide que si vous avez sélectionné **A - Attendre la notification** comme valeur du **Mode d’exécution** dans la page **Gestionnaire de connexions** de l’éditeur. Pour plus d’informations, consultez [SAP BW Source Editor &#40;Connection Manager Page&#41;](sap-bw-source-editor-connection-manager-page.md).  
  
 **ID de demande**  
 Spécifiez l’ID de demande dont vous voulez réinitialiser l’état sur « V - Vert » quand vous cliquez sur **Réinitialiser**.  
  
 **Réinitialiser**  
 Vous permet de réinitialiser l'état de l'ID de demande spécifié sur « V - Vert », après l'invite de confirmation. Ce peut être utile lorsqu'un problème est survenu et que le système SAP Netweaver BW a marqué la demande avec un état jaune ou rouge.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de Source SAP BW &#40;Page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Éditeur de Source SAP BW &#40;Page colonnes&#41;](sap-bw-source-editor-columns-page.md)   
 [Éditeur de source SAP BW &#40;page Sortie d’erreur&#41;](sap-bw-source-editor-error-output-page.md)   
 [Microsoft Connector 1.1 pour SAP BW F1 Aide](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  