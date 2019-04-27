---
title: Connecter une Application de Service PowerPivot à une Application Web SharePoint dans l’Administration centrale | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a5da8e29-7ffd-44e7-bf61-344fa5bea8ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 33d2f83b1b003e6be2fc5c47b8a0e12b440f537c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62749427"
---
# <a name="connect-a-powerpivot-service-application-to-a-sharepoint-web-application-in-central-administration"></a>Connecter une application de service PowerPivot à une application Web SharePoint dans l'Administration centrale
  Une application de service PowerPivot peut être utilisée par les applications Web SharePoint de la batterie de serveurs. Pour rendre une application de service PowerPivot disponible, vous devez l'ajouter à une liste d'association de services.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une application de service PowerPivot dans le groupe par défaut pour garantir que le tableau de bord de gestion PowerPivot fonctionne correctement. N'ajoutez pas plusieurs applications de service PowerPivot au groupe par défaut. L'ajout de plusieurs entrées du même type d'application de service n'est pas une configuration prise en charge et risque de provoquer des erreurs. Si vous créez des applications de service supplémentaires, ajoutez-les aux listes personnalisées.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Ajouter l’Application de service PowerPivot au groupe par défaut](#default)  
  
 [Ajouter l’Application de service PowerPivot une liste d’Association de services personnalisée](#custom)  
  
##  <a name="default"></a> Ajouter l’Application de service PowerPivot au groupe par défaut  
 Une liste d'association de services est une liste de services partagés qui fournissent des ressources à d'autres applications Web SharePoint de la batterie de serveurs. Il existe un groupe par défaut d'association de services pour la batterie de serveurs.  
  
 Pour faire figurer une application de service PowerPivot dans la liste, vous pouvez l'ajouter, soit lorsque vous créez l'application, soit ultérieurement en effectuant la procédure suivante.  
  
1.  Dans Administration centrale, dans **Gestion des applications**, cliquez sur **Configurer les paramètres d'application de service**.  
  
2.  Dans Groupe de proxy d'application, cliquez sur **valeur par défaut**.  
  
3.  Activez la case à cocher en regard de l'application de service PowerPivot (signalée par la valeur `PowerPivot Service Application Proxy` pour le nom de type). Si vous disposez de plusieurs applications de service PowerPivot, choisissez-en une seule.  
  
4.  Cliquez sur **OK**.  
  
##  <a name="custom"></a> Ajouter l’Application de service PowerPivot une liste d’Association de services personnalisée  
 Le groupe par défaut peut être remplacé par une liste personnalisée. Une liste personnalisée est créée spécifiquement pour une application Web SharePoint précise. Elle remplace le groupe par défaut par les associations de services spécifiées par un administrateur de batterie de serveurs ou de service. Si vous avez créé plusieurs applications de service PowerPivot, vous devez utiliser une liste personnalisée pour spécifier l'application à utiliser. Une liste personnalisée ne peut pas être réutilisée par d'autres applications Web. Elle s'applique uniquement à l'application Web pour laquelle elle a été créée.  
  
1.  Dans Administration Centrale, sous **Gestion des applications**, cliquez sur **Gérer les applications Web**.  
  
2.  Sélectionnez l'application (par exemple, SharePoint -80).  
  
3.  Dans Applications Web, dans Gérer, cliquez sur **Connexions aux services**.  
  
4.  Dans **Modifier le groupe suivant de connexions**, sélectionnez **[personnalisé]**.  
  
5.  Activez la case à cocher en regard de chaque connexion d'application de service que vous souhaitez utiliser. Si vous disposez de plusieurs applications de service PowerPivot (signalées par la valeur `PowerPivot Service Application Proxy` pour Type), veillez à n'en choisir qu'une seule.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et configurer une Application de Service PowerPivot dans l’Administration centrale](create-and-configure-power-pivot-service-application-in-ca.md)   
 [Configuration initiale &#40;PowerPivot pour SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)  
  
  
