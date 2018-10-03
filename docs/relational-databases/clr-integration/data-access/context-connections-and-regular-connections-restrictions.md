---
title: Restrictions sur les connexions normales et contextuelles | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 800ec59fb837b167b1bcbffc61ddf7e8ce695849
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641787"
---
# <a name="context-connections-and-regular-connections---restrictions"></a>Connexions contextuelles et connexions standard - Restrictions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique traite des restrictions associées à l’exécution de code dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] processus via des connexions normales et contextuelles.  
  
## <a name="restrictions-on-context-connections"></a>Restrictions applicables aux connexions contextuelles  
 Lorsque vous développez votre application, prenez en considération les restrictions suivantes qui s'appliquent aux connexions contextuelles :  
  
-   Vous ne pouvez avoir qu'une seule connexion contextuelle ouverte à tout moment pour une connexion donnée. Si plusieurs instructions s'exécutent simultanément dans des connexions séparées, chacune d'elles peut obtenir sa propre connexion contextuelle. La restriction n'affecte pas les demandes simultanées à partir de connexions différentes ; elle affecte seulement une demande donnée sur une connexion donnée.  
  
-   Multiple Active Result Sets (MARS) n'est pas pris en charge dans une connexion contextuelle.  
  
-   Le **SqlBulkCopy** classe ne fonctionne pas dans une connexion de contexte.  
  
-   Le traitement par lot des mises à jour dans une connexion contextuelle n'est pas pris en charge  
  
-   **SqlNotificationRequest** ne peut pas être utilisé avec les commandes qui s’exécutent sur une connexion de contexte.  
  
-   L'annulation des commandes qui s'exécutent contre la connexion contextuelle n'est pas prise en charge. Le **SqlCommand.Cancel** méthode ignore la demande.  
  
-   Aucun autre mot clé de chaîne de connexion ne peut être utilisé lorsque vous utilisez « context connection=true ».  
  
-   Le **SqlConnection.DataSource** propriété retourne null si la chaîne de connexion pour le **SqlConnection** est « connexion contextuelle = true », au lieu du nom de l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Définition de la **SqlCommand.CommandTimeout** propriété n’a aucun effet lorsque la commande est exécutée sur une connexion de contexte.  
  
## <a name="restrictions-on-regular-connections"></a>Restrictions applicables aux connexions normales  
 Lorsque vous développez votre application, prenez en considération les restrictions suivantes qui s'appliquent aux connexions normales :  
  
-   L'exécution de commande asynchrone contre des serveurs internes n'est pas prise en charge. Y compris « async = true » dans la chaîne de connexion d’une commande, puis exécuter la commande, entraîne la **System.NotSupportedException** levée. Le message suivant apparaît : « Le traitement asynchrone n'est pas pris en charge en cas d'exécution à l'intérieur du processus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ».  
  
-   **SqlDependency** objet n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
