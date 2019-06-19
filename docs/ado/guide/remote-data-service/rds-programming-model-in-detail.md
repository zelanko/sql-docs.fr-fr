---
title: Modèle de programmation RDS en détail | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS programming model [ADO], details
ms.assetid: 3e57af8d-519b-4467-a0bd-af468534cefd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 55f5d599ea2399697a0b96cc3d316776179b7562
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699585"
---
# <a name="rds-programming-model-in-detail"></a>Modèle de programmation RDS en détail
Les éléments clés du modèle de programmation RDS sont les suivantes :  
  
-   RDS.DataSpace  
  
-   RDSServer.DataFactory  
  
-   RDS.DataControl  
  
-   Événement  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="rdsdataspace"></a>RDS.DataSpace  
 Votre application cliente doit spécifier le serveur et le programme de serveur à appeler. En retour, votre application reçoit une référence au programme serveur et peut traiter la référence comme s’il s’agissait du programme serveur lui-même.  
  
 Le modèle objet RDS fournit cette fonctionnalité avec le [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) objet.  
  
 Le programme du serveur est spécifié avec un identificateur de programme, ou *ProgID*. Le serveur utilise le *ProgID* et le Registre du serveur pour rechercher des informations sur le programme à exécuter.  
  
 Services Bureau à distance établit une distinction en interne selon que le serveur soit sur un serveur distant via Internet ou un intranet ; un serveur sur un réseau local ; ou pas sur un serveur du tout, mais au lieu de cela sur une bibliothèque de liens dynamiques (DLL) locale. Cette distinction détermine comment les informations sont échangées entre le client et le serveur et fait la différence tangible dans le type de référence retourné à votre application cliente. Toutefois, à partir de votre point de vue, cette distinction n’a aucune signification spéciale. Qui importe est que vous recevez une référence de programme utilisable.  
  
## <a name="rdsserverdatafactory"></a>RDSServer.DataFactory  
 Services Bureau à distance fournit un programme de serveur par défaut capable d’exécuter une requête SQL sur la source de données et un retour un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) de l’objet ou de prendre un **Recordset** de l’objet et de mettre à jour de la source de données.  
  
 Le modèle objet RDS fournit cette fonctionnalité avec le [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objet.  
  
 En outre, cet objet a une méthode de création vide **Recordset** objet que vous pouvez remplir par programmation ([CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)) et une autre méthode pour convertir un **Recordset**  objet en une chaîne de texte pour générer une page Web ([ConvertToString](../../../ado/reference/rds-api/converttostring-method-rds.md)).  
  
 Avec ADO, vous pouvez remplacer certains de la connexion standard et le comportement de commande de la **RDSServer.DataFactory** avec un **DataFactory** gestionnaire et un fichier de personnalisation qui contient la connexion, commande et les paramètres de sécurité.  
  
 Le programme du serveur est parfois appelé un *objet métier*. Vous pouvez écrire votre propre objet métier personnalisé qui peut effectuer compliqué accès aux données, vérifications de validité et ainsi de suite. Même lorsque vous écrivez un objet métier personnalisé, vous pouvez créer une instance d’un **RDSServer.DataFactory** et que vous utilisez certaines de ses méthodes pour réaliser vos propres tâches.  
  
## <a name="rdsdatacontrol"></a>RDS.DataControl  
 Services Bureau à distance fournit un moyen de combiner les fonctionnalités de la **RDS. DataSpace** et **RDSServer.DataFactory**et également activer des contrôles visuels d’utiliser facilement les **Recordset** objet retourné par une requête à partir d’une source de données. Tente de services Bureau à distance, pour la plupart des cas, à faire autant que possible accéder aux informations sur un serveur et l’afficher dans un contrôle visuel.  
  
 Le modèle objet RDS fournit cette fonctionnalité avec le [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet.  
  
 Le **RDS. DataControl** présente deux aspects. Un aspect se rapporte à la source de données. Si vous définissez la commande et les informations de connexion à l’aide du **Connect** et **SQL** propriétés de la **RDS. DataControl**, il utilisera automatiquement le **RDS. DataSpace** pour créer une référence à la valeur par défaut **RDSServer.DataFactory** objet. Le **RDSServer.DataFactory** utilisera le **Connect** valeur de propriété pour se connecter à la source de données, utilisez le **SQL** valeur de propriété à obtenir un  **Recordset** à partir de la source de données et retournent le **Recordset** de l’objet à le **RDS. DataControl**.  
  
 Le second aspect porte sur l’affichage de retourné **Recordset** informations dans un contrôle visuel. Vous pouvez associer un contrôle visuel avec le **RDS. DataControl** (dans un processus appelé liaison) et accéder aux informations dans associé **Recordset** objet, en affichant les résultats de requête dans une page Web dans Microsoft® Internet Explorer. Chaque **RDS. DataControl** objet lie une **Recordset** objet représentant les résultats d’une seule requête, à un ou plusieurs contrôles visuels (par exemple, une zone de texte, zone de liste déroulante, contrôle de grille et ainsi de suite). Il peut y avoir plusieurs **RDS. DataControl** objet sur chaque page. Chaque **RDS. DataControl** objet peut être connecté à une autre source de données et contenir les résultats d’une requête distincte.  
  
 Le **RDS. DataControl** objet possède également ses propres méthodes de navigation, de tri et filtrage des lignes d’associé **Recordset** objet. Ces méthodes sont similaires, mais que les méthodes sur l’ADO **Recordset** objet.  
  
## <a name="events"></a>Events  
 Services Bureau à distance prend en charge deux de ses propres événements, qui sont indépendantes du modèle d’événements ADO. Le [onReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) événement est appelé chaque fois que le **RDS. DataControl** [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) propriété change, vous avertissant ainsi quand une opération asynchrone est terminée avec succès, arrêtée ou a rencontré une erreur. Le [onError](../../../ado/reference/rds-api/onerror-event-rds.md) événement est appelé chaque fois qu’une erreur se produit, même si l’erreur se produit pendant une opération asynchrone.  
  
> [!NOTE]
>  Microsoft Internet Explorer fournit deux événements supplémentaires pour les services Bureau à distance : **onDataSetChanged**, ce qui indique que le **Recordset** est fonctionnel mais l’extraction de lignes, et  **onDataSetComplete**, ce qui indique que le **Recordset** a fini d’extraire des lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de programmation RDS avec des objets](../../../ado/guide/remote-data-service/rds-programming-model-with-objects.md)   
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace, objet (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [Scénario RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Didacticiel RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Utilisation et sécurité de RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)



