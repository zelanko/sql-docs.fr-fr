---
title: 'Leçon 2 : ajout d’une référence Web | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e455dd25c2b5d4ffa28bd2bdc28ff679861f1f1d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011413"
---
# <a name="lesson-2-adding-a-web-reference"></a>Leçon 2 : Ajout d’une référence web
  La découverte de service Web est le processus suivant lequel un client recherche un service Web et obtient sa description. Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], le processus de la découverte de service Web implique l'interrogation d'un site Web suivant un algorithme prédéterminé. L'objectif de ce processus est de rechercher la description du service, qui correspond à un document XML utilisant le langage WSDL (Web Services Description Language).  
  
 La description du service décrit les services disponibles et la manière d'interagir avec ces derniers. Sans une description de service, il est impossible d'interagir par programme avec un service Web.  
  
 Votre application doit pouvoir communiquer avec le service Web et le rechercher lors de l'exécution. L'ajout d'une référence Web à votre projet pour le service Web permet cela en générant une classe proxy qui joue le rôle d'interface avec le service Web et qui en fournit une représentation locale. Pour plus d'informations, consultez « Procédure : générer un XML d'un proxy de service Web » dans la documentation [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-add-a-web-reference"></a>Pour ajouter une référence Web  
  
1.  Dans le menu **projet** , cliquez sur **Ajouter une référence de service**.  
  
2.  Dans la boîte de dialogue **Ajouter une référence de service** , cliquez sur **avancé**.  
  
3.  Dans la boîte de dialogue **paramètres de référence de service** , cliquez sur Ajouter une **référence Web**.  
  
4.  Dans la zone **URL** de la boîte de dialogue **Ajouter une référence Web** , tapez l’URL permettant d’obtenir la description de service du service Web Report Server, telle que http://localhost/reportserver/reportservice2010.asmx . Cliquez ensuite sur le bouton **OK** pour récupérer des informations sur le service Web.  
  
     \- ou -  
  
     Si le service Web Report Server existe sur l’ordinateur local, cliquez sur le lien **services Web sur l’ordinateur local** dans le volet navigateur. Cliquez ensuite sur le lien du service Web ReportService2010 dans la liste fournie.  
  
5.  Dans la zone nom de la **référence Web** , renommez la référence Web en ReportService2010, qui est l’espace de noms que vous allez utiliser pour cette référence Web.  
  
6.  Cliquez sur **Ajouter une référence** pour ajouter une référence Web pour le service Web cible.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] télécharge la description du service et génère une classe proxy pour jouer le rôle d'interface entre votre application et le service Web Report Server. Vous devrez également ajouter une référence à l'espace de noms <xref:System.Web.Services> pour que votre référence Web fonctionne.  
  
7.  Dans le menu Projet, cliquez sur **Ajouter une référence**.  
  
8.  Dans la boîte de dialogue **Ajouter une référence** , dans l'onglet **.NET** , sélectionnez **System.Web.Services**, puis cliquez sur **OK**.  
  
 Pour plus d’informations, consultez [Accès à l’API SOAP](../reporting-services/report-server-web-service/accessing-the-soap-api.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Service web Report Server](../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Leçon 3 : accès au service Web](../../2014/tutorials/lesson-3-accessing-the-web-service.md)   
 [Accès au service Web Report Server à l’aide de Visual Basic ou du didacticiel Visual C&#35; &#40;SSRS&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
