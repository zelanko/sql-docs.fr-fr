---
title: "CreateObject (méthode) (RDS) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aeca3cd5d525a3712511a3d7fd59f82210c041e0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="createobject-method-rds"></a>CreateObject (méthode) (RDS)
Crée le proxy pour l’objet métier cible et retourne un pointeur vers elle. Les packages et marshale données proxy pour le stub côté serveur pour les communications avec l’objet métier à envoyer des demandes et des données sur Internet. Pour les objets de composant in-process, aucun proxy ne sont utilisés, seul un pointeur vers l’objet est fourni.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
 Service de données distant prend en charge les protocoles suivants : HTTP, HTTPS (HTTP over Secure Socket Layer), DCOM et dans le processus.  
  
|Protocole|Syntaxe|  
|--------------|------------|  
|HTTP|Set object = DataSpace.CreateObject("ProgId", "http://awebsrvr")|  
|HTTPS|Set object = DataSpace.CreateObject("ProgId", "https://awebsrvr")|  
|DCOM|Set object = DataSpace.CreateObject("ProgId", "computername")|  
|In-process|Set object = DataSpace.CreateObject("ProgId", "")|  
  
## <a name="parameters"></a>Paramètres  
 *Objet*  
 Une variable objet qui correspond à un objet qui est le type spécifié dans *ProgID*.  
  
 *DataSpace*  
 Une variable objet qui représente un [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) objet utilisé pour créer une instance du nouvel objet.  
  
 *ProgID*  
 A **chaîne** valeur qui contient l’identificateur programmatique spécifiant un objet métier côté serveur qui implémente les règles d’entreprise de votre application.  
  
 *awebsrvr* ou *Nom_Ordinateur*  
 A **chaîne** valeur qui représente une URL qui identifie le serveur Web des Internet Information Services (IIS) sur lequel une instance de l’objet métier du serveur est créée.  
  
## <a name="remarks"></a>Notes  
 Le *protocole HTTP* est le protocole Web standard ; *HTTPS* est un protocole Web sécurisé. Utilisez le *protocole DCOM* lorsque vous exécutez un réseau local sans protocole HTTP. Le *intra-processus* protocole est une bibliothèque de liens dynamiques (DLL) locale ; il n’utilise pas un réseau.  
  
## <a name="applies-to"></a>S'applique à  
 [DataSpace, objet (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [L’objet DataFactory, méthode de requête et exemple de CreateObject (méthode) (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [DataSpace et la méthode CreateObject exemple (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [CreateRecordset, méthode (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


