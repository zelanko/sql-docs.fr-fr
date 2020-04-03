---
title: Créer un rapport lié | Microsoft Docs
description: Découvrez comment créer un rapport lié pour créer des versions supplémentaires d’un rapport existant.
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cb362f699e8bf87e0f386c3ec726869f67aec934
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510160"
---
# <a name="create-a-linked-report"></a>Créer un rapport lié
  Un rapport lié est un élément de serveur de rapports qui fournit un point d'accès à un rapport existant. Au niveau conceptuel, il est assimilable au raccourci d'un programme que vous utilisez pour exécuter une application ou ouvrir un fichier.  
  
 Un rapport lié est issu d'un rapport existant et il reste fidèle à la définition de rapport d'origine. Il hérite toujours des propriétés de la source de données et de la mise en page du rapport d'origine. Toutes les autres propriétés et toutes les autres valeurs peuvent différer, notamment la sécurité, les paramètres, l'emplacement, les abonnements et les planifications.  
  
 Vous créez un rapport lié lorsque vous voulez créer des versions supplémentaires d'un rapport existant. Ainsi, vous pouvez trouver pratique d'utiliser un rapport de ventes régional unique pour créer des rapports spécifiques aux régions pour tous vos secteurs de ventes.  
  
 Bien que les rapports liés soient généralement basés sur des rapports paramétrés, il n'est pas obligatoire de recourir à des rapports paramétrés. Vous pouvez créer des rapports liés dès lors que vous souhaitez déployer un rapport existant avec des paramètres différents.  
  
## <a name="to-create-a-linked-report"></a>Pour créer un rapport lié  
  
1. Dans le portail web, accédez au rapport souhaité, cliquez dessus avec le bouton droit, puis sélectionnez **Gérer** dans le menu déroulant.

2. Dans la page **Gérer <reportname>** , sélectionnez **Créer un rapport lié**.  
  
3. Saisissez un nom pour le nouveau rapport lié. Entrez éventuellement une description.  
  
4. Pour sélectionner un autre dossier pour le rapport, cliquez sur le bouton des points de suspension (...) à droite de ***Emplacement***.  Accédez au nouveau dossier du rapport, puis sélectionnez **Sélectionner**. Si vous ne sélectionnez pas un autre dossier, le rapport lié est créé dans le dossier actif.  
  
5. Sélectionnez **Create** (Créer). Le rapport lié est créé.  

6. Sous **Avancé**, sélectionnez une autre valeur **Délai d’expiration du rapport** si vous le souhaitez, puis sélectionnez **Appliquer** pour enregistrer les modifications.
  
     L'icône d'un rapport lié est différente des autres éléments gérés par un serveur de rapports. L'icône ci-après indique un rapport lié :  
  
     ![Icône Rapport lié](../../reporting-services/report-server/media/hlp-16linked.gif "Icône Rapport lié")  
  
## <a name="see-also"></a>Voir aussi  

 [Concepts de Reporting Services &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)  
 [Le portail web d’un serveur de rapports (Mode natif SSRS)](../../reporting-services/web-portal-ssrs-native-mode.md)
  
