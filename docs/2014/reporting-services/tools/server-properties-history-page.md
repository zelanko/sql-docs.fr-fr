---
title: Propriétés du serveur (page Historique) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.history.f1
ms.assetid: be9d8018-a46f-4625-9ae1-138ebe6b38ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c10649c3dbe873464bcc52ca5bc54e5b948d547a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63157595"
---
# <a name="server-properties-history-page"></a>Propriétés du serveur (page Historique)
  Utilisez cette page pour définir le nombre de copies par défaut que l'historique de rapport peut conserver. La valeur par défaut fournit un paramètre initial qui établit les limites de l'historique de tous les rapports. Ces paramètres sont modifiables pour chaque rapport.  
  
 L'historique de rapport est une collection d'instantanés de rapport qui incluent des données de rapport et une mise en page qui s'appliquent au rapport au moment où l'instantané est créé. Vous pouvez utiliser l'historique de rapport pour garder une copie d'un rapport tel qu'il se présentait à une date ou heure spécifique. Vous pouvez créer et gérer l'historique de rapport pour des rapports individuels qui s'exécutent sur un serveur de rapports en mode natif ou configuré pour le mode intégré SharePoint.  
  
 Les instantanés d'historique de rapport sont stockés dans la base de données du serveur de rapports. Si vous conservez un nombre illimité d'instantanés, veillez à vérifier régulièrement la taille de la base de données pour vous assurer qu'elle n'augmente pas trop rapidement ni n'utilise trop d'espace disque.  
  
 Pour ouvrir cette page, démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à une instance de serveur de rapports, cliquez avec le bouton droit sur le nom du serveur de rapports, puis sélectionnez **Propriétés**. Cliquez sur **Historique** pour ouvrir cette page.  
  
## <a name="options"></a>Options  
 **Conserver un nombre illimité d'instantanés dans l'historique de rapport**  
 Conservez tous les instantanés d'historique de rapport. Vous devez supprimer manuellement des instantanés pour réduire la taille de l'historique de rapport.  
  
 **Limiter les copies de l'historique de rapport**  
 Conservez un nombre défini d'instantanés d'historique de rapport. Lorsque la limite est atteinte, des copies anciennes sont supprimées de l'historique de rapport pour libérer de l'espace pour les nouvelles copies.  
  
 Si vous limitez l'historique de rapport ultérieurement, le serveur de rapports applique la nouvelle limite à l'historique de rapport existant dès que celui-ci la dépasse. Les instantanés de rapport les plus anciens sont supprimés en premier. Si l'historique de rapport est vide ou n'a pas atteint la limite, de nouveaux instantanés de rapport sont ajoutés. Lorsque la limite est atteinte, l'instantané le plus ancien est supprimé dès qu'un nouvel instantané est ajouté.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir les propriétés du serveur de rapports &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Se connecter à un serveur de rapports dans Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Aide du serveur de rapports dans Management Studio via la touche F1](report-server-in-management-studio-f1-help.md)  
  
  
