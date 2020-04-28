---
title: Exécution de l’exemple d’application de carnet d’adresses | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 3a2644e9-d634-4ae6-a5b7-13fb7b317ec7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 45324642d2f323297ecbe091617fbb14cc5fc785
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922249"
---
# <a name="running-the-address-book-sample-application"></a>Exécution de l’exemple d’application Carnet d’adresses
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Pour exécuter l’application Carnet d’adresses, procédez comme suit.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-run-this-application"></a>Pour exécuter cette application  
  
1.  Assurez-vous que Microsoft SQL Server est en cours d’exécution. Cliquez sur **Démarrer**, pointez sur tous les **programmes**, pointez sur **Microsoft SQL Server 7,0**, puis cliquez sur **Service Manager**. S’il y a une flèche verte dans le cercle blanc, SQL Server est en cours d’exécution. Si ce n’est pas le cas (il y aura un carré rouge dans le cercle blanc), cliquez sur **Démarrer/Continuer**.  
  
2.  Dans Microsoft Internet Explorer 4,0 ou version ultérieure, tapez l’adresse suivante :  
  
     **https://** *WebServer* **/RDS/AddressBook/AddrBook.asp**  
  
     où *serveur* Web est le nom du serveur Web sur lequel sont installés les composants du serveur RDS.  
  
3.  Vous pouvez ensuite essayer différents scénarios dans l’exemple d’application de carnet d’adresses, par exemple en recherchant une personne en fonction de son nom de messagerie électronique, en répertoriant toutes les personnes ayant le titre « responsable de programme » ou en modifiant des enregistrements existants. Cliquez sur **Rechercher** pour remplir la grille de données avec tous les noms disponibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de liaison de données de l’application Carnet d’adresses](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)




