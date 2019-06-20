---
title: Changer le type d’attribut (Complément MDS pour Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ecdbff5b071ae82fe8bd8322c1ef9d46f153b0cc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65488904"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a>Modifier le type d'attribut (complément MDS pour Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], les administrateurs peuvent modifier le type d’attribut lorsque le type de données ou le nombre de caractères autorisé est incorrect.  
  
 Si vous souhaitez modifier le type d’attribut pour créer une liste contrainte (attribut basé sur un domaine), consultez [Créer un attribut basé sur un domaine &#40;Complément MDS pour Exce&#41;](../../master-data-services/microsoft-excel-add-in/create-a-domain-based-attribute-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas mettre à jour le type ou la longueur des colonnes **Nom** ou **Code**.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder aux zones fonctionnelles **Administration de système** et **Explorateur** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md).  
  
-   Un modèle, une entité et un attribut doivent exister.  
  
### <a name="to-change-the-attribute-type"></a>Pour modifier le type d'attribut  
  
1.  Dans Excel, chargez l'entité qui contient la colonne (attribut) que vous souhaitez modifier. Pour plus d’informations, consultez [Exporter des données dans Excel depuis Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
2.  Cliquez sur une cellule de la colonne que vous souhaitez modifier.  
  
3.  Dans le groupe **Modèle de build** , cliquez sur **Propriétés d'attribut**.  
  
4.  Dans la boîte de dialogue **Propriétés d'attribut** , mettez à jour les paramètres si nécessaire.  
  
5.  Cliquez sur **OK**.  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a>Que se passe-t-il lorsque vous modifiez le type d'attribut ?  
 S’il existe une dépendance sur l’attribut, par exemple si l’attribut est référencé par une règle d’entreprise MDS ou par une hiérarchie dérivée, vous ne pouvez pas modifier le type de données de l’attribut. Vous obtenez un message d’erreur indiquant que le type d’attribut ne peut pas être modifié car il est référencé par un objet.  
  
 En cas d’erreur pendant la conversion du type de données pour les valeurs d’attribut, MDS exécute les opérations suivantes.  
  
-   Modifie le type de données de l’attribut.  
  
-   Génère une copie de l’attribut avec le suffixe « _old » qui contient les valeurs précédentes. Il s’agit de ce que l’on appelle un attribut déconseillé.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs &#40;Master Data Services&#41;](../../master-data-services/attributes-master-data-services.md)   
 [Génération d’un modèle &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/building-a-model-mds-add-in-for-excel.md)  
  
  
