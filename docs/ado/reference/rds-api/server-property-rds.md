---
title: Server, propriété (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
f1_keywords:
- RDS::IBindMgr21::Server
helpviewer_keywords:
- Server property [RDS]
ms.assetid: d2727ce7-da9f-4271-ae3c-9334ef477c14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77ad00d9c21a7f7558f8f5cafc66464c1ffc54f7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63217644"
---
# <a name="server-property-rds"></a>Server, propriété (RDS)
Indique le protocole de nom et la communication Internet Information Services (IIS).  
  
 Vous pouvez définir le **Server** propriété au moment du design dans les balises d’objet de la[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) de l’objet ou au moment de l’exécution dans le code de script.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
 **HTTP**  
  
 Syntaxe au moment de la conception  
  
```  
  
<PARAM NAME="Server" VALUE="http:  
//awebsrvr:port  
">  
  
```  
  
 Syntaxe de l’exécution  
  
```  
  
DataControl  
.Server="https://  
awebsrvr:port  
"  
  
```  
  
 **HTTPS**  
  
 Syntaxe au moment de la conception  
  
```  
  
<PARAM NAME="Server" VALUE="https://awebsrvr:port">  
```  
  
 Syntaxe de l’exécution  
  
```  
  
DataControl.Server="https://awebsrvr:port"  
```  
  
 **DCOM**  
  
 Syntaxe au moment de la conception  
  
```  
  
<PARAM NAME="Server" VALUE="  
computername  
">  
  
```  
  
 Syntaxe de l’exécution  
  
```  
  
DataControl.Server="computername"  
```  
  
 **Dans le processus**  
  
 Syntaxe au moment de la conception  
  
```  
  
<PARAM NAME="Server" VALUE="">  
  
```  
  
 Syntaxe de l’exécution  
  
```  
  
DataControl.Server=""  
```  
  
## <a name="parameters"></a>Paramètres  
 *awebsrvr*or *computername*  
 Un **chaîne** valeur contenant un Internet ou le chemin d’accès de l’intranet ou le nom de l’ordinateur, si le serveur se trouve sur un ordinateur distant ; ou une chaîne vide si le serveur se trouve sur l’ordinateur local.  
  
 *port*  
 Facultatif. Un port qui est utilisé pour se connecter à un serveur exécutant IIS. Le numéro de port est défini dans Internet Explorer (sur le **vue** menu, cliquez sur **Options**, puis sélectionnez le **connexion** onglet) ou dans IIS.  
  
 *DataControl*  
 Une variable objet qui représente un **RDS. DataControl** objet.  
  
## <a name="remarks"></a>Notes  
 Le serveur est l’emplacement où le **RDS. DataControl** demande (autrement dit, une requête ou une mise à jour) est traitée. Par défaut, toutes les demandes sont traitées par le [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objet, [MSDFMAP. Gestionnaire](../../../ado/guide/remote-data-service/datafactory-customization.md) composant, et [MSDFMAP. INI](../../../ado/guide/remote-data-service/understanding-the-customization-file.md) fichier sur le serveur spécifié. N’oubliez pas que lors de la modification des serveurs afin de rapprocher des paramètres dans les nouvelles et anciennes **MSDFMAP. INI** fichiers. Incompatibilités peuvent entraîner des requêtes qui aboutissent sur un serveur échoue sur un autre. Si la propriété de serveur est définie sur la chaîne vide « », ces objets seront utilisés sur l’ordinateur local.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété de serveur (VBScript)](../../../ado/reference/rds-api/server-property-example-vbscript.md)   
 [Se connecter, propriété (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Propriété SQL](../../../ado/reference/rds-api/sql-property.md)   
 [SubmitChanges, méthode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


