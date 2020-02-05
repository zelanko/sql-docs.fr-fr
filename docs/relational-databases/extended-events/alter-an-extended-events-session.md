---
title: Modifier une session d'événements étendus
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 32a57c46cebb17df257f2002c25ab5f1d7107379
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "75255770"
---
# <a name="alter-an-extended-events-session"></a>Modifier une session d'événements étendus

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Après avoir créé une session d'événements étendus, vous pouvez la modifier en fonction de vos besoins à l'aide de l' **Assistant Événements étendus SQL Server**.  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Vous ne pouvez pas modifier une cible pour les sessions actives et inactives, et vous ne pouvez pas modifier les configurations avancées de propriétés pour une session active.  
  
 Vous pouvez apporter les modifications suivantes aux sessions d'événements actives et inactives :  
  
-   Ajouter ou supprimer des événements de la session, puis modifier les configurations des événements, telles que les champs d'événement, les filtres et les actions.  
  
-   Ajouter ou supprimer une cible de la session d'événements.  
  
-   Activer l'option **Démarrer la session d'événements au démarrage du serveur** .  
  
 Vous pouvez apporter les modifications supplémentaires suivantes à une session d'événements inactive :  
  
-   Activer l'option **Suivre la relation entre les événements** .  
  
-   Modifier la configuration de propriétés avancée.  
  
> [!NOTE]  
>  L’ **Assistant Événements étendus SQL Server** ne prend pas en charge la modification de la session d’événements.  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a>Comment modifier une session d'événements étendus à l'aide de l'Assistant Événements étendus SQL Server  
  
-   Dans l'Explorateur d'objets, développez **Gestion**, **Événements étendus**, puis **Sessions**.  
  
-   Cliquez avec le bouton droit sur la session à modifier, puis cliquez sur **Propriétés**.  
  
-   Dans la boîte de dialogue **Propriétés** , apportez les modifications appropriées, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [Créer une session d'événements étendus à l'aide de l'éditeur de requête](quick-start-extended-events-in-sql-server.md)  
  
  
