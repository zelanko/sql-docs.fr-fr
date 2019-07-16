---
title: ConnectionString, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionString
helpviewer_keywords:
- ConnectionString property [ADO]
ms.assetid: 3be75b75-4d36-4479-ab64-9a456869252a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e391ad7c61bd6c303b0558892435af344a2768fb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933499"
---
# <a name="connectionstring-property-ado"></a>ConnectionString, propriété (ADO)
Indique les informations utilisées pour établir une connexion à une source de données.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **ConnectionString** propriété pour spécifier une source de données en passant une chaîne de connexion détaillée contenant une série de *argument* *= value* instructions séparées par points-virgules.  
  
 ADO prend en charge cinq arguments pour le **ConnectionString** propriété ; n’importe quel autre pass arguments directement au fournisseur sans aucun traitement par ADO. Les arguments ADO prend en charge est les suivantes.  
  
|Argument|Description|  
|--------------|-----------------|  
|*Provider=*|Spécifie le nom d’un fournisseur à utiliser pour la connexion.|  
|*Nom du fichier =*|Spécifie le nom d’un fichier spécifique au fournisseur (par exemple, un objet de source de données persistantes) contenant des informations de connexion prédéfinies.|  
|*Fournisseur distant =*|Spécifie le nom d’un fournisseur à utiliser lors de l’ouverture d’une connexion côté client. (Service de données distant uniquement.)|  
|*Serveur distant =*|Spécifie le nom de chemin d’accès du serveur à utiliser lors de l’ouverture d’une connexion côté client. (Service de données distant uniquement.)|  
|*URL =*|Spécifie la chaîne de connexion comme une URL absolue identifiant une ressource, comme un fichier ou répertoire.|  
  
 Après avoir défini le **ConnectionString** propriété et ouvrez le [connexion](../../../ado/reference/ado-api/connection-object-ado.md) de l’objet, le fournisseur peut modifier le contenu de la propriété, par exemple, en mappant les noms d’arguments définis par ADO à leur équivalents pour le fournisseur spécifique.  
  
 Le **ConnectionString** propriété hérite automatiquement de la valeur utilisée pour le *ConnectionString* argument de la [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) (méthode), afin que vous puissiez remplacer actuel **ConnectionString** propriété pendant la **Open** appel de méthode.  
  
 Étant donné que le *nom de fichier* argument provoque ADO charger le fournisseur associé, vous ne pouvez pas passer à la fois le *fournisseur* et *nom de fichier* arguments.  
  
 Le **ConnectionString** propriété est en lecture/écriture lorsque la connexion est fermée et en lecture seule lorsqu’il est ouvert.  
  
 Les doublons d’un argument dans le **ConnectionString** propriété sont ignorées. La dernière instance de n’importe quel argument est utilisée.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** lorsqu’il est utilisé sur une côté client **connexion** objet, le **ConnectionString** propriété peut inclure uniquement les *fournisseur distant* et *serveur distant* paramètres.  
  
 Le tableau suivant répertorie le fournisseur ADO par défaut pour chaque système d’exploitation Windows :  
  
|Fournisseur de ADO par défaut|Système d’exploitation de Windows|  
|--------------------------|------------------------------|  
|MSDASQL<br /><br /> (Pour améliorer la lisibilité du code source, spécifier explicitement le nom du fournisseur dans la chaîne de connexion.)|Windows 2000 (32 bits)<br /><br /> Windows XP (32 bits)<br /><br /> Windows 2003 Server (32 bits)<br /><br /> Windows Vista (32 bits)<br /><br /> Windows Vista Service Pack 1 ou version ultérieure (32 bits et 64 bits)<br /><br /> Versions de Windows après Windows Vista (32 bits et 64 bits)|  
|Sans valeur par défaut.<br /><br /> Lorsqu’une application ADO s’exécute sur les systèmes d’exploitation suivants et ne spécifie pas le fournisseur de manière explicite, ADO renvoie l’erreur suivante : « ADODB. Connexion : fournisseur n’est pas spécifié, et il n’existe aucun fournisseur désigné par défaut »|Windows 2000 (64 bits)<br /><br /> Windows XP (64 bits)<br /><br /> Windows 2003 Server (64 bits)<br /><br /> Windows Vista (64 bits)|  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ConnectionString, ConnectionTimeout et les propriétés State, exemple (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout et les propriétés State, exemple (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Annexe A : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
