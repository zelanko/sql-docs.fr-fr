---
description: Configuration de RDS
title: Configuration des services Bureau à distance | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS configuration [ADO]
ms.assetid: 5dd48483-858a-48c2-98ce-f2359abe1f59
author: rothja
ms.author: jroth
ms.openlocfilehash: 23110157445da6c776de7582682992ab55a97ac8
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759877"
---
# <a name="configuring-rds"></a>Configuration de RDS
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Pour implémenter RDS efficacement, veillez à vous familiariser avec les différentes configurations disponibles. Cette section contient des informations importantes sur la sécurité et l’évolutivité dans votre implémentation de RDS. Consultez les rubriques suivantes pour plus d’informations sur la configuration de vos ordinateurs pour utiliser RDS.  
  
-   [Octroi de privilèges d’invité à un serveur web](./granting-guest-privileges-to-a-web-server-computer.md)  
  
-   [Inscription d’un objet métier personnalisé](./registering-a-custom-business-object.md)  
  
-   [Marquage d’objets métier comme sûrs pour l’écriture de scripts](./marking-business-objects-as-safe-for-scripting.md)  
  
-   [Inscription d’objets métier sur le client en vue d’une utilisation avec DCOM](./registering-business-objects-on-the-client-for-use-with-dcom.md)  
  
-   [Définition du format pour le marshaling de flux DCOM](./setting-dcom-stream-marshaling-format.md)  
  
-   [Configuration d’une DLL pour s’exécuter sur DCOM](./enabling-a-dll-to-run-on-dcom.md)  
  
-   [Configuration de serveurs virtuels sur IIS](./configuring-virtual-servers-on-iis.md)  
  
-   [Sécurisation des applications RDS](./securing-rds-applications.md)  
  
-   [Configuration de DataFactory en mode sans échec ou unrestricted](./configuring-datafactory-for-safe-or-unrestricted-modes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des technologies associées avec RDS](./using-related-technologies-with-rds.md)   
 [Personnalisation de DataFactory](./datafactory-customization.md)   
 [Résolution des problèmes liés à RDS](./troubleshooting-rds.md)