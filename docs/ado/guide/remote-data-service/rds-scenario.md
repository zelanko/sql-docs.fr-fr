---
title: Scénario RDS | Microsoft Docs
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
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45e0f3be43ce8e2780268b7dfde83253b71da946
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539706"
---
# <a name="rds-scenario"></a>Scénario RDS
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 L’application de carnet d’adresses est un scénario qui vous montre comment utiliser le Service de données à distance (RDS) pour générer une application Web simple, prenant en charge les données - un carnet d’adresses d’entreprise en ligne. Ce scénario est utile pour Microsoft Visual Basic Scripting Edition (VBScript) et les programmeurs COM qui veulent apprendre à utiliser les contrôles ActiveX prenant en charge les données avec les services Bureau à distance et des logiciels plus expérimentés les développeurs qui souhaitent générer des applications Web orientées données.  
  
 Ce scénario suppose que vous savez comment utiliser des balises de mise en page HTML, les techniques de liaison de données utilisez DHTML et programme base avec des contrôles ActiveX.  
  
 Si vous avez installé le Kit de développement, vous trouverez le code source complet pour l’exemple d’application Carnet d’adresses dans le répertoire du Kit de développement logiciel au samples\dataaccess\rds\AddressBook\AddressBook.asp. Pour afficher le scénario de carnet d’adresses, dans Internet Explorer 4.0 ou version ultérieure, tapez **https://*webserver*/RDS/AddressBook/AddressBook.asp** où *webserver* est le nom Étant donné sur votre ordinateur serveur Windows NT 4.0 ou Windows 2000 Web qui exécute Internet Information Services (IIS) et ASP.  
  
## <a name="introduction-to-address-book"></a>Introduction au carnet d’adresses  
 L’exemple d’application Carnet d’adresses fournit un carnet d’adresses en ligne simple que vous pouvez utiliser pour publier un répertoire de recherche via un intranet. Le carnet d’adresses est conçu afin qu’un utilisateur peut entrer une chaîne de recherche dans un ou plusieurs champs pour demander des informations sur les employés. Pour vous montrer les fonctionnalités de base du Service de données distant, l’exemple d’application est intentionnellement réduite, avec un nombre minimal d’objets et des champs de recherche.  
  
 L’interface de l’application se compose des éléments suivants :  
  
-   Un élément non visuel **RDS. DataControl** objet de liaison de données qui est utilisé par le client pour se connecter à la base de données.  
  
-   Critères de recherche de zones de texte HTML qui agissent en tant que champs d’entrée pour l’attribut de l’employé.  
  
-   HTML des boutons de commande pour générer des requêtes, effacer les champs de recherche, mettre à jour de la base de données avec les informations sur les employés, annuler des modifications en attente et parcourir les lignes de données affichées dans la grille.  
  
-   DHTML une liaison de données pour afficher les données retournées par les requêtes sur une base de données back-end (via le **RDS. DataControl** objet de liaison de données) dans une table.  
  
-   Routines de VBScript qui se connectent chacun des éléments qui ont été mentionnés précédemment et leur permettent d’interagir. Le code VBScript est également utilisé pour initialiser le **RDS. DataControl** de l’objet et de créer dynamiquement les en-têtes de colonne dans la table HTML dans les noms de la **RDS. DataControl** champs du recordset.  
  
 Suivez les liens à partir de l’étape à l’étape pour configurer et exécuter le scénario et pour en savoir plus sur le fonctionne du scénario.  
  
 Ce scénario contient les rubriques suivantes.  
  
-   [Configuration système exigée pour l’application Carnet d’adresses](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)  
  
-   [Exécution du script SQL Carnet d’adresses](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)  
  
-   [Exécution de l’exemple d’application Carnet d’adresses](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)  
  
-   [Objet de liaison de données de l’application Carnet d’adresses](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)  
  
-   [Boutons de commande de l’application Carnet d’adresses](../../../ado/guide/remote-data-service/address-book-command-buttons.md)  
  
-   [Boutons de navigation de l’application Carnet d’adresses](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration système requise pour l’Application de carnet d’adresses](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)   
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Principes de base RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Didacticiel RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)


