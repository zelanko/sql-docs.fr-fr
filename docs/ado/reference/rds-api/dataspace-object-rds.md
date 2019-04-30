---
title: DataSpace, objet (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace object [RDS]
ms.assetid: 9194bffa-5bdf-4dff-af86-f7158c23bfa7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d75a5dcd8a09388c031e4e01c8bb8b9c1d62bb80
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63134483"
---
# <a name="dataspace-object-rds"></a>DataSpace, objet (RDS)
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Crée des proxys côté client pour les objets métier personnalisés situés sur la couche intermédiaire.  
  
 Remote Data Service nécessite des proxys d’objets métier afin que les composants côté client peuvent communiquer avec les objets métiers sur la couche intermédiaire. Les proxys permettent l’empaquetage, 8369Les et le de transport (marshaling) de l’application [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) données au-delà des limites de processus ou l’ordinateurs.  
  
 Service de données distant utilise le **RDS. DataSpace** l’objet [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) méthode pour créer des proxys d’objets métier. Le proxy de l’objet est créé dynamiquement chaque fois qu’une instance de son équivalent d’objet métier de couche intermédiaire est créée. Service de données distant prend en charge les protocoles suivants : HTTP, HTTPS (HTTP Secure Sockets), DCOM et in-process (composants du client et l’objet métier que résident sur le même ordinateur).  
  
> [!NOTE]
>  Services Bureau à distance se comporte de manière « sans état » lorsque le **RDS. DataSpace** objet utilise les protocoles HTTP ou HTTPS. Autrement dit, des informations internes sur une demande du client sont ignorées une fois que le serveur retourne une réponse.  
  
> [!NOTE]
>  Bien que l’objet métier semble exister pour la durée de vie du proxy d’objet métier, l’objet métier existe réellement uniquement jusqu'à ce qu’une réponse est envoyée à une demande. Quand une demande est émise (autrement dit, une méthode est appelée sur l’objet métier), le proxy ouvre une nouvelle connexion au serveur et le serveur crée une nouvelle instance de l’objet métier. Une fois que l’objet métier répond à la demande, le serveur détruit l’objet métier et ferme la connexion.  
  
> [!NOTE]
>  Ce comportement signifie que vous ne peut pas passer des données d’une requête à un autre à l’aide d’une propriété de l’objet métier ou une variable. Vous devez utiliser un autre mécanisme, tel qu’un fichier ou un argument de méthode, pour rendre persistantes les données d’état.  
  
 L’ID de classe pour le **RDS. DataSpace** objet est 0-983A-00C04FC29E36 BD96C556 65A3 - 11 D.  
  
 Le **DataSpace** objet est sécurisé pour le script.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet DataSpace (RDS)](../../../ado/reference/rds-api/dataspace-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DataSpace (exemple d’objet) et CreateObject (exemple de méthode) (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)


