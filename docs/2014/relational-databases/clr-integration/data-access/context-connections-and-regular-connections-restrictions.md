---
title: Restrictions sur les connexions normales et contextuelles | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 3b721409f0915cb1e13861f6481909e02af37cb2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919168"
---
# <a name="restrictions-on-regular-and-context-connections"></a>Restrictions applicables aux connexions normales et contextuelles
  Cette rubrique traite des restrictions associées à l’exécution de code dans le [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] processus via des connexions normales et contextuelles.  
  
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
  
-   L'exécution de commande asynchrone contre des serveurs internes n'est pas prise en charge. L'inclusion de « async=true » dans la chaîne de connexion d'une commande, suivie de l'exécution de cette commande, lève l'exception `System.NotSupportedException`. Ce message s’affiche : « Traitement asynchrone n’est pas pris en charge lors de l’exécution à l’intérieur de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] processus. »  
  
-   L'objet `SqlDependency` n'est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion contextuelle](context-connection.md)  
  
  
