---
title: Description du code XML d’un flux de travail personnalisé (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a71ee85fc4dce4abd7d8ef91a8f22529ce8d5a0f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483012"
---
# <a name="custom-workflow-xml-description-master-data-services"></a>Description personnalisée XML de flux de travail (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], la méthode <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> est appelée par le service d'intégration de flux de travail MDS SQL Server lors du démarrage d'un flux de travail. Cette méthode reçoit les métadonnées et les données relatives à l'élément qui a déclenché la règle d'entreprise de flux de travail sous la forme d'un bloc XML. Pour découvrir un exemple de code qui implémente un gestionnaire de flux de travail, consultez [Exemple de flux de travail personnalisé &#40;Master Data Services&#41;](create-a-custom-workflow-example.md).  
  
 L'exemple suivant montre à quoi ressemble le code XML envoyé au gestionnaire de flux de travail :  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 Le tableau suivant décrit quelques-unes des balises contenues dans ce code XML :  
  
|Tag|Description|  
|---------|-----------------|  
|\<Type>|Texte que vous avez entré dans la zone de texte **Type de flux de travail** dans [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] pour identifier quels assemblys personnalisés de flux de travail doivent être chargés.|  
|\<SendData>|Valeur booléenne contrôlée par la case à cocher **Inclure les données de membre dans le message** dans [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. La valeur 1 indique que la section \<MemberData> est envoyée ; sinon la section \<MemberData> n’est pas envoyée.|  
|<Server_URL>|Texte que vous avez entré dans la zone de texte **Site du flux de travail** dans [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|  
|<Action_ID>|Texte que vous avez entré dans la zone de texte **Nom du flux de travail** dans [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|  
|\<MemberData>|Contient les données du membre qui a déclenché l'action de flux de travail. Cela est inclus uniquement si la valeur de \<SendData> est 1.|  
|\<Entrez*xxx*>|Cet ensemble de balises contient des métadonnées sur la création du membre, comme sa date de création et la personne qui l'a créé.|  
|\<LastChg*xxx*>|Cet ensemble de balises contient des métadonnées sur la dernière modification apportée au membre, comme la date de la modification et la personne qui l'a effectuée.|  
|\<Name>|Premier attribut du membre qui a été modifié. Cet exemple de membre contient uniquement des attributs Name et Code.|  
|\<Code>|Attribut suivant du membre qui a été modifié. Si cet exemple de membre contenait plus d'attributs, ils suivraient celui-ci.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un &#40;de flux de travail personnalisé Master Data Services&#41;](create-a-custom-workflow-master-data-services.md)   
 [Exemple de flux de travail personnalisé &#40;Master Data Services&#41;](create-a-custom-workflow-example.md)  
  
  
