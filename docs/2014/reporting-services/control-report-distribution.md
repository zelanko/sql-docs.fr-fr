---
title: Contrôler la distribution des rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], report distribution
- subscriptions [Reporting Services], e-mail
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- subscriptions [Reporting Services], security
- mail [Reporting Services]
ms.assetid: 8f15e2c6-a647-4b05-a519-1743b5d8654c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de8a27801ef89f10bf303cee17d1c2d0e1081c5a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109699"
---
# <a name="control-report-distribution"></a>Contrôler la distribution des rapports
  Vous pouvez configurer un serveur de rapports de façon à réduire les risques de sécurité associés à la remise par messagerie électronique ou dans un partage de fichiers.  
  
## <a name="securing-reports"></a>Sécurisation des rapports  
 La première étape du contrôle de la distribution des rapports consiste à sécuriser le rapport contre les accès non autorisés. Pour être utilisé dans un abonnement, un rapport doit utiliser un ensemble stocké d'informations d'identification qui ne varie pas pour les remises individuelles. Tout utilisateur pouvant accéder à un rapport sur le serveur de rapports peut l'exécuter et éventuellement le distribuer. Pour empêcher cela, vous devez limiter l'accès au rapport aux seuls utilisateurs qui en ont besoin. Pour plus d’informations, consultez [sécuriser les rapports et les ressources](security/secure-reports-and-resources.md) et [sécuriser les dossiers](security/secure-folders.md).  
  
 Les rapports hautement confidentiels qui utilisent la sécurité de la base de données pour autoriser l'accès ne peuvent pas être distribués par voie d'abonnement.  
  
> [!IMPORTANT]  
>  Les rapports sont véhiculés comme des fichiers. Les risques et les sécurités qui s'appliquent aux fichiers s'appliquent de la même façon aux rapports qui sont enregistrés sur disque ou envoyés comme pièces jointes. Tout utilisateur pouvant accéder à un fichier peut distribuer ou utiliser le fichier à sa guise.  
  
## <a name="controlling-e-mail-delivery"></a>Contrôle de la remise par messagerie  
 Vous pouvez configurer un serveur de rapports de façon à limiter la distribution par messagerie à des domaines hôtes spécifiques. Par exemple, vous pouvez empêcher un serveur de rapports de remettre un rapport à tous les domaines, sauf à ceux répertoriés dans le fichier de configuration RSReportServer.  
  
 Vous pouvez également définir des paramètres de configuration pour masquer le champ **À** dans un abonnement. Dans ce cas, les rapports sont remis uniquement à l'utilisateur qui définit l'abonnement. Toutefois, une fois qu'un rapport a été envoyé à un utilisateur, vous ne pouvez pas explicitement l'empêcher d'être transféré.  
  
 La façon la plus efficace de contrôler la distribution des rapports consiste à configurer un serveur de rapports de sorte qu'il n'envoie qu'une adresse URL de serveur de rapports. Le serveur de rapports utilise l'authentification Windows et le modèle d'autorisation par rôle pour contrôler l'accès à un rapport. Si un utilisateur reçoit accidentellement par courrier électronique un rapport qu'il n'est pas autorisé à consulter, le serveur de rapports n'affiche pas le rapport.  
  
## <a name="controlling-file-share-delivery"></a>Contrôle de la remise par partage de fichiers  
 La remise par partage de fichiers permet d'envoyer un rapport à un fichier sur un disque dur. Une fois le fichier enregistré sur disque, il n'est plus soumis au modèle de sécurité basée sur les rôles que le serveur de rapports utilise pour contrôler l'accès utilisateur. Pour protéger un rapport qui a été distribué sur un disque, placez des ACL (Access Control Lists) sur le fichier lui-même ou sur le dossier qui le contient. D'autres options de sécurité sont disponibles en fonction de votre système d'exploitation.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de rapports pour la remise par messagerie &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Abonnements et remise &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Créer et gérer des abonnements pour les serveurs de rapports en mode natif](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md)  
  
  
