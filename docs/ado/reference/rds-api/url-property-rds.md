---
title: URL, propriété (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d4093321edfca7d1176c4b5be18ee876888b1a2
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600031"
---
# <a name="url-property-rds"></a>URL, propriété (RDS)
Indique une chaîne qui contient une URL relative ou absolue.  
  
 Vous pouvez définir le **URL** propriété au moment du design dans le [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) de l’objet de balise ou au moment de l’exécution dans le code de script.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Server*  
 Un **chaîne** valeur qui contient une URL valide.  
  
 *DataControl*  
 Une variable objet qui représente un **DataControl** objet.  
  
## <a name="remarks"></a>Notes  
 En règle générale, l’URL identifie un fichier ASP (.asp) qui peut produire et renvoyer un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Par conséquent, l’utilisateur peut obtenir un **Recordset** sans avoir à invoquer le côté serveur [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) de l’objet, ou bien programmer un objet métier personnalisé.  
  
 Si le **URL** propriété a été définie, [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) soumettra des modifications à l’emplacement spécifié par l’URL.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [URL, exemple de propriété (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


