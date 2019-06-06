---
title: Objet de liaison de données de carnet d’adresses | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS scenarios [ADO], data-binding object
- address book application scenario [ADO], data-binding object
ms.assetid: 080c1925-d453-4b89-92ac-c93591490518
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 31efe56dcb5ae926d5da08aa00a1005597b17b91
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718619"
---
# <a name="address-book-data-binding-object"></a>Objet de liaison de données de l’application Carnet d’adresses
L’application de carnet d’adresses utilise le [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) objet pour lier des données à partir de la base de données SQL Server à un objet visuel (dans ce cas, un tableau DHTML) dans la page de l’application client HTML. La logique du programme VBScript pilotée par événements utilise le [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) à :  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
-   Interroger la base de données, envoyer des mises à jour à la base de données et actualiser la grille de données.  
  
-   Autoriser les utilisateurs à accéder au premier, ensuite, précédente, ou le dernier enregistrement dans la grille de données.  
  
 Le code suivant définit la **RDS. DataControl** composant :  
  
```vb
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=DC1 Width=1 Height=1>  
   <PARAM NAME="SERVER" VALUE="https://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=sqloledb;  
Initial Catalog=AddrBookDb;Integrated Security=SSPI;">  
</OBJECT>  
```  
  
 La balise OBJECT définit le **RDS. DataControl** composant dans le programme. La balise comprend deux types de paramètres :  
  
-   Ceux associés à la balise d’objet générique.  
  
-   Ceux propres à la **RDS. DataControl** objet.  
  
## <a name="generic-object-tag-parameters"></a>Paramètres de balise d’objet générique  
 Le tableau suivant décrit les paramètres associés à la balise OBJECT.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|***CLASSID***|Un nombre unique de 128 bits qui identifie le type d’objet incorporé dans le système. Cet identificateur est conservé dans le Registre système de l’ordinateur local. (Pour les ID de classe de la **RDS. DataControl** d’objets, consultez [RDS. DataControl, objet](../../../ado/reference/rds-api/datacontrol-object-rds.md).)|  
|***ID***|Définit un identificateur de document à l’échelle pour l’objet incorporé est utilisé pour l’identifier dans le code.|  
  
## <a name="rdsdatacontrol-tag-parameters"></a>RDS. Paramètres de la balise de DataControl  
 Le tableau suivant décrit les paramètres spécifiques à la **RDS. DataControl** objet. (Pour obtenir la liste complète de la **RDS. DataControl** de l’objet et savoir quand les implémenter, consultez [RDS. DataControl, objet](../../../ado/reference/rds-api/datacontrol-object-rds.md).)  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[SERVER](../../../ado/reference/rds-api/server-property-rds.md)|Si vous utilisez HTTP, la valeur est le nom de l’ordinateur serveur précédé par `https://`.|  
|[CONNECT](../../../ado/reference/rds-api/connect-property-rds.md)|Fournit les informations de connexion nécessaires pour le **RDS. DataControl** pour se connecter à SQL Server.|  
|[SQL](../../../ado/reference/rds-api/sql-property.md)|Définit ou retourne la chaîne de requête utilisée pour récupérer le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Boutons de commande de l’application Carnet d’adresses](../../../ado/guide/remote-data-service/address-book-command-buttons.md)


