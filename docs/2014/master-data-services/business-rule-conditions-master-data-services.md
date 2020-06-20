---
title: Conditions de règle d’entreprise (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d2e0a8c3-4c2e-407c-856e-68d95ebda9ed
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 12ba98331d2002dab10d462398f7e77389888e32
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972129"
---
# <a name="business-rule-conditions-master-data-services"></a>Conditions de règle d'entreprise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les conditions de règle d'entreprise déterminent les conditions qui doivent être réunies pour qu'une ou plusieurs actions soient entreprises.  
  
> [!NOTE]  
>  Les conditions sont facultatives. Si vous ne spécifiez pas de condition, les actions sont entreprises à chaque fois que les données sont validées par rapport aux règles d'entreprise.  
  
## <a name="business-rule-conditions"></a>Conditions de règle d'entreprise  
  
|Nom de la condition|Description|  
|--------------------|-----------------|  
|**est égal à**|L'attribut sélectionné **est égal à** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte, nombre, date et lien.|  
|**n'est pas égal à**|L'attribut sélectionné **n'est pas égal à** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte, nombre, date et lien.|  
|**est supérieur à**|L'attribut sélectionné **est supérieur à** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte, nombre et date.|  
|**est supérieur ou égal à**|L'attribut sélectionné **est supérieur ou égal à** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte, nombre et date.|  
|**est inférieur à**|L'attribut sélectionné **est inférieur à** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte, nombre et date.|  
|**est inférieur ou égal à**|L'attribut sélectionné **est inférieur ou égal à** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte, nombre et date.|  
|**commence par**|L'attribut sélectionné **commence par** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte et de lien.|  
|**se termine par**|L'attribut sélectionné **se termine par** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte et de lien.|  
|**contains**|L'attribut sélectionné **contient** un attribut spécifique, une valeur d'attribut spécifique, ou est vide.<br /><br /> Cette condition est valide pour les valeurs de texte et de lien.|  
|**contient le modèle**|L'attribut sélectionné **contient le modèle** d'un attribut spécifique, d'une valeur d'attribut spécifique, ou est vide. Utilisez des expressions régulières .NET Framework pour spécifier le modèle.<br /><br /> Pour plus d'informations sur les expressions régulières, consultez [Éléments du langage des expressions régulières](https://go.microsoft.com/fwlink/?LinkId=164401) dans MSDN Library.<br /><br /> Cette condition est valide pour les valeurs de texte et de lien.|  
|**contient le sous-ensemble**|L'attribut sélectionné **contient le sous-ensemble** d'un attribut spécifique ou d'une valeur d'attribut spécifique. Vous devez spécifier la position de départ pour la recherche (par exemple, 1 signifie que la recherche débute au premier caractère).<br /><br /> Cette condition est valide pour les valeurs de texte et de lien.|  
|**a changé**|L'attribut sélectionné **a changé** depuis la dernière application des règles d'entreprise au membre. Vous devez spécifier le groupe de modification dont l'attribut est membre.<br /><br /> Pour plus d’informations sur les groupes de suivi des modifications, consultez [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](add-attributes-to-a-change-tracking-group-master-data-services.md).<br /><br /> Cette condition est valide pour les valeurs de texte, nombre, date et lien.|  
|**est compris entre**|L'attribut sélectionné **est compris entre** deux valeurs d'attribut spécifiques.<br /><br /> Cette condition est valide pour les valeurs de texte, nombre et date.|  
  
> [!NOTE]  
>  Lorsqu'une règle d'entreprise contenant une condition qui compare deux valeurs est appliquée à un membre pour lequel les deux valeurs sont NULL, la validation de ce membre échoue.  
  
## <a name="see-also"></a>Voir aussi  
 [Actions de règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/business-rule-actions-master-data-services.md)   
 [&#40;des règles d’entreprise Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)   
 [Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)  
  
  
