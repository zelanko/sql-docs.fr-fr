---
title: "Configurer un pare-feu pour l’accès FILESTREAM | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: blob
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Firewall [Database Engine], FILESTREAM
- FILESTREAM [SQL Server], Windows Firewall
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 150e9f40e31cce3027bfb6637ecbdd0b7dee4117
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2018
---
# <a name="configure-a-firewall-for-filestream-access"></a>Configurer un pare-feu pour l'accès FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Pour pouvoir utiliser FILESTREAM dans un environnement protégé par un pare-feu, le client et le serveur doivent être en mesure de résoudre les noms DNS sur le serveur qui contient les fichiers FILESTREAM. FILESTREAM requiert l'ouverture des ports 139 et 445 dédiés au partage de fichiers Windows.  
  
### <a name="to-open-the-windows-file-sharing-ports-on-a-computer-that-is-running-windows-7"></a>Pour ouvrir les ports de partage de fichiers Windows sur un ordinateur qui exécute Windows 7  
  
1.  Dans le Panneau de configuration, ouvrez **Pare-feu Windows**.  
  
2.  Dans le volet gauche, cliquez sur **Paramètres avancés**. Si vous êtes invité à entrer un mot de passe administrateur ou à fournir une confirmation, tapez le mot de passe ou fournissez la confirmation.  
  
3.  Dans la boîte de dialogue **Pare-feu Windows avec fonctions avancées de sécurité** , dans le volet gauche, cliquez sur **Règles de trafic entrant**, puis, dans le volet droit, cliquez sur **Nouvelle règle**.  
  
4.  Suivez les instructions de l'Assistant Nouvelle règle de trafic entrant pour ajouter le port TCP 139.  
  
5.  Répétez l'étape précédente pour ajouter le port TCP 445.  
  
6.  Fermez la boîte de dialogue **Pare-feu Windows avec fonctions avancées de sécurité** .  
  
  
