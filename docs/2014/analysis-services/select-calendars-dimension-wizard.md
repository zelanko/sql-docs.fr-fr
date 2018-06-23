---
title: Sélectionner des calendriers (Assistant Dimension) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dimensionwizard.serverSpecialCalendars.f1
ms.assetid: 6e28a020-2586-4b13-9333-b499fb1b33af
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6796c7c3064adc65982b1d5aaec005249e224cae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044550"
---
# <a name="select-calendars-dimension-wizard"></a>Sélectionner des calendriers (Assistant Dimension)
  La page **Sélectionner des calendriers** permet de créer des hiérarchies supplémentaires représentant les calendriers fiscaux, de rapports, de fabrication ou ISO (International Standards Organization) 8601 de la dimension de temps.  
  
> [!NOTE]  
>  Cette page s’affiche uniquement si vous avez sélectionné **Dimension de temps du serveur** dans la page **Sélectionner le type de la dimension** ou **Construire la dimension sans utiliser de source de données** dans la page **Définition de dimension** et sélectionné **Dimension de temps** dans la page **Sélectionnez le type de la dimension** .  
  
## <a name="options"></a>Options  
 **Calendrier fiscal**  
 Sélectionnez cette option pour créer une hiérarchie de temps en fonction d'un calendrier fiscal.  
  
 **Jour et mois de départ**  
 Sélectionnez le jour et le mois de début du calendrier fiscal.  
  
> [!NOTE]  
>  Cette option est disponible uniquement quand **Calendrier fiscal** est sélectionné.  
  
 **Convention d’affectation de noms de calendrier fiscal**  
 Sélectionnez la convention de nom utilisée par le calendrier fiscal. Sélectionnez **Nom de l’année civile** ou **Nom de l’année civile + 1**.  
  
> [!NOTE]  
>  Cette option est disponible uniquement quand **Calendrier fiscal** est sélectionné.  
  
 **Calendrier de rapport (ou du marketing)**  
 Sélectionnez cette option pour créer une hiérarchie de temps en fonction d'un calendrier de rapports.  
  
 **Semaine et mois de départ**  
 Sélectionnez la semaine et le mois de début du calendrier de rapports.  
  
> [!NOTE]  
>  Cette option est disponible uniquement quand **Calendrier rapports (ou marketing)** est sélectionné.  
  
 **Semaine du mois**  
 Sélectionnez le modèle de semaine du mois utilisé par le calendrier des rapports.  
  
> [!NOTE]  
>  Cette option est disponible uniquement quand **Calendrier rapports (ou marketing)** est sélectionné.  
  
 Le tableau suivant répertorie les options disponibles pour le modèle de semaine du mois.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Semaine 445**|Le premier mois du trimestre compte 4 semaines, le deuxième mois en compte 4, et le troisième mois en compte 5.|  
|**Semaine 454**|Le premier mois du trimestre compte 4 semaines, le deuxième mois en compte 5, et le troisième mois en compte 4.|  
|**Semaine 544**|Le premier mois du trimestre a 5 semaines, le deuxième mois du trimestre a 4 semaines et le troisième mois du trimestre a 4 semaines.|  
  
 **Calendrier de production**  
 Sélectionnez cette option pour créer une hiérarchie de temps en fonction d'un calendrier de fabrication.  
  
 **Semaine et mois de départ**  
 Sélectionnez la semaine et le mois de début du calendrier de fabrication.  
  
> [!NOTE]  
>  Cette option est disponible uniquement quand **Calendrier de fabrication** est sélectionné.  
  
 **Trimestre avec des périodes supplémentaires**  
 Sélectionnez ou tapez le trimestre qui doit contenir les périodes supplémentaires.  
  
> [!NOTE]  
>  Cette option est disponible uniquement quand **Calendrier de fabrication** est sélectionné.  
  
 **Calendrier ISO 8601**  
 Sélectionnez cette option pour créer une hiérarchie en fonction du calendrier ISO 8601.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  