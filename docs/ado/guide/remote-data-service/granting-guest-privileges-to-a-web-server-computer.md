---
description: Octroi de privilèges d’invité à un serveur web
title: Octroi de privilèges d’invité à un ordinateur serveur Web | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: rothja
ms.author: jroth
ms.openlocfilehash: 9fa62e95920e8a4aece0f7b6833c635cfdbf7b09
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452181"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Octroi de privilèges d’invité à un serveur web
Le compte de serveur Web anonyme (IUSR_*ComputerName*) doit être ajouté au groupe local invités sur l’ordinateur serveur Web pour utiliser RDS.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Pour accorder des privilèges d’invité à un ordinateur serveur Web  
  
1.  Sur votre ordinateur Microsoft Windows 2000 Server, cliquez sur **Démarrer**, pointez sur **programmes**, sur **Outils d’administration**, puis cliquez sur gestion de l' **ordinateur**.  
  
2.  Dans l’arborescence de la console, dans **utilisateurs et groupes locaux**, cliquez sur **groupes**.  
  
3.  Sélectionnez le groupe local **invités** . Dans le menu **action** , choisissez **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés des invités** , cliquez sur **Ajouter**.  
  
5.  Si le compte du serveur Web anonyme n’apparaît pas dans la liste de la boîte de dialogue **Sélectionner les utilisateurs ou les groupes** , tapez son nom (IUSR_*ComputerName*) dans la zone inférieure vide, puis cliquez sur **Ajouter**.  
  
6.  Cliquez sur **OK**.


