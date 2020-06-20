---
title: Restrictions sur les connexions régulières et de contexte | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 2ebf188db7213b26264d66bad7e2a4ca9f0a09af
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970669"
---
# <a name="restrictions-on-regular-and-context-connections"></a>Restrictions applicables aux connexions normales et contextuelles
  Cette rubrique décrit les restrictions associées au code qui s’exécute dans le [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] processus via le contexte et les connexions normales.  
  
## <a name="restrictions-on-context-connections"></a>Restrictions applicables aux connexions contextuelles  
 Lorsque vous développez votre application, prenez en considération les restrictions suivantes qui s'appliquent aux connexions contextuelles :  
  
-   Vous ne pouvez avoir qu'une seule connexion contextuelle ouverte à tout moment pour une connexion donnée. Si plusieurs instructions s'exécutent simultanément dans des connexions séparées, chacune d'elles peut obtenir sa propre connexion contextuelle. La restriction n'affecte pas les demandes simultanées à partir de connexions différentes ; elle affecte seulement une demande donnée sur une connexion donnée.  
  
-   Multiple Active Result Sets (MARS) n'est pas pris en charge dans une connexion contextuelle.  
  
-   La classe `SqlBulkCopy` ne fonctionne pas dans une connexion contextuelle.  
  
-   Le traitement par lot des mises à jour dans une connexion contextuelle n'est pas pris en charge  
  
-   `SqlNotificationRequest` ne peut pas être utilisé avec les commandes qui s'exécutent contre une connexion contextuelle.  
  
-   L'annulation des commandes qui s'exécutent contre la connexion contextuelle n'est pas prise en charge. La méthode `SqlCommand.Cancel` ignore la demande silencieusement.  
  
-   Aucun autre mot clé de chaîne de connexion ne peut être utilisé lorsque vous utilisez « context connection=true ».  
  
-   La propriété `SqlConnection.DataSource` retourne NULL si la chaîne de connexion pour le `SqlConnection` est « context connection=true », au lieu du nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   La définition de la propriété `SqlCommand.CommandTimeout` n'a aucun effet lorsque la commande est exécutée contre une connexion contextuelle.  
  
## <a name="restrictions-on-regular-connections"></a>Restrictions applicables aux connexions normales  
 Lorsque vous développez votre application, prenez en considération les restrictions suivantes qui s'appliquent aux connexions normales :  
  
-   L'exécution de commande asynchrone contre des serveurs internes n'est pas prise en charge. L'inclusion de « async=true » dans la chaîne de connexion d'une commande, suivie de l'exécution de cette commande, lève l'exception `System.NotSupportedException`. Le message suivant apparaît : « Le traitement asynchrone n'est pas pris en charge en cas d'exécution à l'intérieur du processus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ».  
  
-   L'objet `SqlDependency` n'est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](context-connection.md)  
  
  
