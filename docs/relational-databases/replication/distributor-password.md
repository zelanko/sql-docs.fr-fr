---
title: Mot de passe du serveur de distribution | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 76143a4158aab90a96b015566bc993a7f70ef0d8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85653389"
---
# <a name="distributor-password"></a>Mot de passe du serveur de distribution
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Si, dans la page **Serveurs de publication** de cet Assistant, vous avez autorisé un ou plusieurs serveurs de publication à utiliser ce serveur comme serveur de distribution distant, vous devez définir un mot de passe pour la connexion que la réplication établit entre le serveur de publication et le serveur de distribution distant à l'aide de la connexion **distributor_admin** . Dans la page **Mot de passe d'administration** de l'Assistant Nouvelle publication ou de l'Assistant Configurer le serveur de distribution, vous devez entrer le même mot de passe pour chaque serveur de publication qui utilise le serveur de distribution. Pour plus d’informations sur la sécurité des serveurs de distribution, consultez [Sécuriser le serveur de distribution](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="options"></a>Options  
 **Mot de passe**  
 Entrez un mot de passe fort pour la connexion entre le serveur de publication et le serveur de distribution distant.  
  
 **Confirmer le mot de passe**  
 Entrez à nouveau le mot de passe pour confirmer la première saisie.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
