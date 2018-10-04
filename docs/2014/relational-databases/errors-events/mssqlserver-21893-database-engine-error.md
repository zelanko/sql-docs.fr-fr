---
title: MSSQLSERVER_21893 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6258f36990efccf83b43e8d8ac8bd4c2397477aa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48212749"
---
# <a name="mssqlserver21893"></a>MSSQLSERVER_21893
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21893|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21893|  
|Texte du message|Les abonnés (%s) du serveur de publication d'origine '%s' n'apparaissent pas en tant que serveurs distants sur le serveur de publication redirigé '%s'. Exécutez `sp_addlinkedserver` du serveur de publication redirigé pour ajouter ces abonnés en tant que serveurs distants.|  
  
## <a name="explanation"></a>Explication  
 `sp_validate_redirected_publisher` utilise les tables de métadonnées d’abonnement de la base de données du serveur de publication sur le serveur distant pour identifier ses abonnés associés et vérifie qu’il existe des entrées associées dans master.dbo.sysservers pour les abonnés. Cette erreur est retournée si des abonnés identifiés ne sont pas présents.  
  
 Elle n'est pas considérée comme une erreur fatale. Les agents qui reçoivent cette erreur vont la consigner dans le journal à titre d'information mais ne vont pas s'arrêter, car l'absence d'entrées d'abonnés appropriées sur le nouveau serveur de publication a un impact limité sur la réplication. Sans une entrée appropriée pour un abonné dans sysservers, certaines activités de gestion d’abonnement peuvent échouer quand elles sont exécutées par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Toutefois, ces mêmes opérations peuvent être effectuées avec succès en exécutant les procédures stockées de gestion explicitement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez `sp_addlinkedserver` sur le serveur de publication redirigé pour chaque abonné identifié afin de l'ajouter en tant que serveur distant. Puis, exécutez `sp_serveroption` pour définir le bit d'abonné pour le serveur.  
  
  
