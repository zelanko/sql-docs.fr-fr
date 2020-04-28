---
title: Restrictions sur les connexions régulières et de contexte | Microsoft Docs
description: Cet article décrit les restrictions associées au code s’exécutant dans le processus de Microsoft SQL Server par le biais de connexions de contexte et normales.
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81485284"
---
# <a name="context-connections-and-regular-connections---restrictions"></a>Connexions contextuelles et connexions standard - Restrictions
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique décrit les restrictions associées au code qui s’exécute dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] processus via le contexte et les connexions normales.  
  
## <a name="restrictions-on-context-connections"></a>Restrictions applicables aux connexions contextuelles  
 Lorsque vous développez votre application, prenez en considération les restrictions suivantes qui s'appliquent aux connexions contextuelles :  
  
-   Vous ne pouvez avoir qu'une seule connexion contextuelle ouverte à tout moment pour une connexion donnée. Si plusieurs instructions s'exécutent simultanément dans des connexions séparées, chacune d'elles peut obtenir sa propre connexion contextuelle. La restriction n'affecte pas les demandes simultanées à partir de connexions différentes ; elle affecte seulement une demande donnée sur une connexion donnée.  
  
-   Multiple Active Result Sets (MARS) n'est pas pris en charge dans une connexion contextuelle.  
  
-   La classe **SqlBulkCopy** ne fonctionne pas dans une connexion contextuelle.  
  
-   Le traitement par lot des mises à jour dans une connexion contextuelle n'est pas pris en charge  
  
-   **SqlNotificationRequest** ne peut pas être utilisé avec des commandes qui s’exécutent sur une connexion contextuelle.  
  
-   L'annulation des commandes qui s'exécutent contre la connexion contextuelle n'est pas prise en charge. La méthode **SqlCommand. Cancel** ignore la demande en mode silencieux.  
  
-   Aucun autre mot clé de chaîne de connexion ne peut être utilisé lorsque vous utilisez « context connection=true ».  
  
-   La propriété **SqlConnection. DataSource** retourne la valeur null si la chaîne de connexion pour **SqlConnection** est « context connection = true », et non le nom de l' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]instance de.  
  
-   La définition de la propriété **SqlCommand. CommandTimeout** n’a aucun effet lorsque la commande est exécutée sur une connexion contextuelle.  
  
## <a name="restrictions-on-regular-connections"></a>Restrictions applicables aux connexions normales  
 Lorsque vous développez votre application, prenez en considération les restrictions suivantes qui s'appliquent aux connexions normales :  
  
-   L'exécution de commande asynchrone contre des serveurs internes n'est pas prise en charge. L’inclusion de « Async = true » dans la chaîne de connexion d’une commande, puis l’exécution de la commande, entraîne la levée de **System. NotSupportedException** . Le message suivant apparaît : « Le traitement asynchrone n'est pas pris en charge en cas d'exécution à l'intérieur du processus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ».  
  
-   L’objet **SqlDependency** n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
