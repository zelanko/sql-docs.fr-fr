---
title: Restrictions sur les connexions régulières et contextuelles (fr) Microsoft Docs
description: Cet article décrit les restrictions associées au code en cours d’exécution dans le processus Microsoft SQL Server par le contexte et les connexions régulières.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: fac92658366cceffc3d4fac5ba650f9a14501185
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81485284"
---
# <a name="context-connections-and-regular-connections---restrictions"></a>Connexions contextuelles et connexions standard - Restrictions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ce sujet traite des restrictions associées [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’exécution du code dans le processus par le contexte et les connexions régulières.  
  
## <a name="restrictions-on-context-connections"></a>Restrictions applicables aux connexions contextuelles  
 Lorsque vous développez votre application, prenez en considération les restrictions suivantes qui s'appliquent aux connexions contextuelles :  
  
-   Vous ne pouvez avoir qu'une seule connexion contextuelle ouverte à tout moment pour une connexion donnée. Si plusieurs instructions s'exécutent simultanément dans des connexions séparées, chacune d'elles peut obtenir sa propre connexion contextuelle. La restriction n'affecte pas les demandes simultanées à partir de connexions différentes ; elle affecte seulement une demande donnée sur une connexion donnée.  
  
-   Multiple Active Result Sets (MARS) n'est pas pris en charge dans une connexion contextuelle.  
  
-   La classe **SqlBulkCopy** ne fonctionne pas dans un contexte.  
  
-   Le traitement par lot des mises à jour dans une connexion contextuelle n'est pas pris en charge  
  
-   **SqlNotificationRequest** ne peut pas être utilisé avec des commandes qui s’exécutent à l’encontre d’une connexion contextuelle.  
  
-   L'annulation des commandes qui s'exécutent contre la connexion contextuelle n'est pas prise en charge. La méthode **SqlCommand.Cancel** ignore silencieusement la demande.  
  
-   Aucun autre mot clé de chaîne de connexion ne peut être utilisé lorsque vous utilisez « context connection=true ».  
  
-   La propriété **SqlConnection.DataSource** revient nulle si la chaîne de connexion pour le **SqlConnection** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]est "contexte connection-true", au lieu du nom de l’instance de .  
  
-   La configuration de la propriété **SqlCommand.CommandTimeout** n’a aucun effet lorsque la commande est exécutée à l’appel d’une connexion contextuelle.  
  
## <a name="restrictions-on-regular-connections"></a>Restrictions applicables aux connexions normales  
 Lorsque vous développez votre application, prenez en considération les restrictions suivantes qui s'appliquent aux connexions normales :  
  
-   L'exécution de commande asynchrone contre des serveurs internes n'est pas prise en charge. L’inclusion de «async-vrai» dans la chaîne de connexion d’une commande, puis l’exécution de la commande, entraîne **System.NotSupportedException** étant jeté. Le message suivant apparaît : « Le traitement asynchrone n'est pas pris en charge en cas d'exécution à l'intérieur du processus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ».  
  
-   **L’objet SqlDependency n’est** pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
