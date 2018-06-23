---
title: Restrictions sur les connexions normales et contextuelles | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f0d266b75dad229a0784606af112c249728a112c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143262"
---
# <a name="restrictions-on-regular-and-context-connections"></a>Restrictions applicables aux connexions normales et contextuelles
  Cette rubrique décrit les restrictions associées à l’exécution de code dans la [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] processus via des connexions normales et contextuelles.  
  
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
  
  