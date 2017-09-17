---
title: "L’Application d’exemple de carnet d’adresses en cours d’exécution | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 3a2644e9-d634-4ae6-a5b7-13fb7b317ec7
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dca092267dfba700e1d079f8d2147c7f204e6e32
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="running-the-address-book-sample-application"></a>L’Application d’exemple de carnet d’adresses en cours d’exécution
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Pour exécuter l’application de carnet d’adresses, suivez cette procédure.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-run-this-application"></a>Pour exécuter cette application  
  
1.  Assurez-vous que Microsoft SQL Server est en cours d’exécution. Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft SQL Server 7.0**, puis cliquez sur **Service Manager**. S’il existe une flèche verte dans le cercle blanc, SQL Server s’exécute. Si elle n’est pas (il y aura un carré rouge dans le cercle blanc), cliquez sur **Démarrer/Continuer**.  
  
2.  Dans Microsoft Internet Explorer 4.0 ou version ultérieure, tapez l’adresse suivante :  
  
     **http://** *webserver* **/RDS/AddressBook/AddrBook.asp**  
  
     où *webserver* est le nom du serveur Web sur lequel sont installés les composants de serveur Services Bureau à distance.  
  
3.  Vous pouvez ensuite essayer différents scénarios dans l’exemple d’application de carnet d’adresses, telles que la recherche d’une personne basé sur son nom de messagerie, qui répertorie toutes les personnes portant le titre « Chef », ou modifier des enregistrements existants. Cliquez sur **trouver** pour remplir la grille de données avec tous les noms disponibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de liaison de données de l’application Carnet d’adresses](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)





