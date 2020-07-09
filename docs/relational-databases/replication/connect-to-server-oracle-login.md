---
title: Se connecter au serveur (Oracle), Connexion | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 22e029a225d46d24730bb16c9ef55a13f676c81e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773944"
---
# <a name="connect-to-server-oracle-login"></a>Se connecter au serveur (Oracle), Connexion
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Utilisez l’onglet **Connexion** de la boîte de dialogue **Se connecter au serveur** pour définir le compte sous lequel les connexions sont effectuées du serveur de distribution [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers le serveur de publication Oracle. Vous devez utiliser le compte défini pour le schéma utilisateur d'administration de réplication au cours de la configuration du serveur de publication. Pour plus d’informations, consultez [Configurer un serveur de publication Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Options  
 **Instance de serveur**  
 Nom TNS (Transparent Network Substrate) du serveur de publication Oracle, défini au cours de la configuration du logiciel client Oracle installé sur le serveur de distribution.  
  
 **Authentification**  
 Sélectionnez **Authentification standard Oracle** (recommandé) ou **Authentification Windows**. Si vous sélectionnez **Authentification Windows**:  
  
-   Le serveur Oracle doit être configuré pour permettre les connexions en utilisant les informations d'identification Windows. Pour plus d'informations, consultez votre documentation Oracle.  
  
-   Vous devez être connecté avec le compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows que vous avez défini pour le schéma utilisateur d'administration de réplication.  
  
 **Connexion** et **Mot de passe**  
 Si vous avez sélectionné **Authentification standard Oracle** pour l'option d' **authentification** , définissez la connexion et le mot de passe à utiliser qui doivent être identiques à ceux du schéma utilisateur d'administration de réplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des termes de la publication Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
