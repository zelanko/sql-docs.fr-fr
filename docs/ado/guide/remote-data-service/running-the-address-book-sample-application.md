---
title: L’Application exemple Carnet d’adresses en cours d’exécution | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922249"
---
# <a name="running-the-address-book-sample-application"></a>Exécution de l’exemple d’application Carnet d’adresses
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Pour exécuter l’application Carnet d’adresses, procédez comme suit.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-run-this-application"></a>Pour exécuter cette application  
  
1.  Assurez-vous que Microsoft SQL Server est en cours d’exécution. Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft SQL Server 7.0**, puis cliquez sur **Service Manager**. S’il existe une flèche verte dans le cercle blanc, puis SQL Server est en cours d’exécution. Si ce n’est pas (il sera un carré rouge dans le cercle blanc), cliquez sur **Démarrer/Continuer**.  
  
2.  Dans Microsoft Internet Explorer 4.0 ou version ultérieure, tapez l’adresse suivante :  
  
     **https://** *webserver* **/RDS/AddressBook/AddrBook.asp**  
  
     où *webserver* est le nom du serveur Web où sont installés les composants de serveur Services Bureau à distance.  
  
3.  Vous pouvez ensuite essayer différents scénarios dans l’exemple d’application Carnet d’adresses, telles que la recherche d’une personne selon son nom de messagerie électronique, répertoriant toutes les personnes portant le titre « Program Manager », ou modifier des enregistrements existants. Cliquez sur **trouver** pour remplir la grille de données avec tous les noms disponibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de liaison de données de l’application Carnet d’adresses](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)




