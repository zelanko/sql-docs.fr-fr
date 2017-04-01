---
title: "Propri&#233;t&#233;s du serveur (page S&#233;curit&#233;) - Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/10/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.reportserver.serverproperties.security.f1"
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 11
---
# Propri&#233;t&#233;s du serveur (page S&#233;curit&#233;) - Reporting Services
  Utilisez cette page [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] dans [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] pour désactiver les fonctionnalités susceptibles de nuire à un serveur de rapports. La désactivation de ces fonctionnalités limitera certaines d'entre elles, mais peut améliorer la sécurité globale du serveur de rapports en atténuant des menaces spécifiques.  
  
 Pour ouvrir cette page :
 1) Démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 2) Connectez-vous à une instance de serveur de rapports.
 3) Cliquez avec le bouton droit sur le nom du serveur de rapports et sélectionnez **Propriétés**. 
 4) Cliquez sur **Sécurité** pour ouvrir cette page.  
  
## Options  
 **Activer la sécurité intégrée Windows pour les sources de données de rapport**  
 Spécifiez si une connexion à une source de données de rapport peut être établie à l'aide du jeton de sécurité Windows de l'utilisateur qui a demandé le rapport.  
  
 Si vous désactivez cette fonctionnalité, la fonctionnalité de sécurité intégrée Windows dans les pages de propriétés de la source de données de rapport ne sera pas disponible. Si les sources de données de rapport sont configurées pour la sécurité intégrée Windows et que vous désactivez par la suite cette fonctionnalité, le serveur de rapports mettra immédiatement à jour toutes les propriétés de connexion à la source de données pour demander des informations d'identification.  
  
 **Activer la génération d'états ad hoc**  
 Spécifiez si les utilisateurs peuvent effectuer des requêtes ad hoc à partir d'un rapport du Générateur de rapports, où les nouveaux rapports sont générés automatiquement lorsqu'un utilisateur clique sur des données d'intérêt.  
  
 La définition de cette option détermine si la propriété **EnableLoadReportDefinition** sur le serveur de rapports a la valeur **True** ou **False**. Si vous désactivez cette option, la propriété aura la valeur **False** et le serveur de rapports ne générera pas les rapports générés interactifs créés pendant l'exploration de données. Tous les appels à la méthode **LoadReportDefinition** seront bloqués.  
  
 La désactivation de cette option atténue la menace qu'un utilisateur malveillant lance une attaque par déni de service en surchargeant le serveur de rapports avec les demandes **LoadReportDefinition** .  
  
## Voir aussi  
 [Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Se connecter à un serveur de rapports dans Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Aide du serveur de rapports dans Management Studio accessible par la touche F1](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)  
  
  