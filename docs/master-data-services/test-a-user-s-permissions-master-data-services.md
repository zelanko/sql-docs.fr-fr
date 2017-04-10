---
title: "Tester les autorisations d&#39;un utilisateur (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
caps.latest.revision: 4
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 4
---
# Tester les autorisations d&#39;un utilisateur (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez créer un utilisateur de test et vous connecter à l'application Web pour tester les autorisations. Lorsqu'un utilisateur tente d'accéder à l'URL [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , les informations d'identification de l'utilisateur sont authentifiées. Dans Internet Explorer, les paramètres de sécurité déterminent si cette opération se produit automatiquement ou si l'utilisateur doit entrer un nom d'utilisateur et un mot de passe. Pour modifier ces paramètres, procédez comme suit :  
  
### Pour tester la sécurité d'un utilisateur  
  
1.  Dans Internet Explorer 7 et version ultérieure, cliquez sur **Outils**, sur **Options Internet**, puis sur l'onglet **Sécurité** .  
  
2.  Cliquez sur **Intranet local** , puis sur le bouton **Personnaliser le niveau** .  
  
3.  Dans la section **Authentification utilisateur** , choisissez **Demander le nom d'utilisateur et le mot de passe**.  
  
4.  La prochaine fois que vous ouvrez la fenêtre de navigateur, vous serez invité à fournir un nom d'utilisateur et un mot de passe.  
  
## Voir aussi  
 [Sécurité &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  