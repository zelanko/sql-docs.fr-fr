---
title: Méthodes ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, methods
- methods [ADO]
ms.assetid: a38c5670-ba28-44f3-bd5b-fcb46880e904
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 67b428a06679bdb0cade14314195d576a1ccc596
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696855"
---
# <a name="ado-methods"></a>Méthodes ADO

|||  
|-|-|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Crée un nouvel enregistrement pour être une mise à jour **Recordset** objet.|  
|[Append](../../../ado/reference/ado-api/append-method-ado.md)|Ajoute un objet à une collection. Si la collection est **champs**, un nouveau **champ** objet peut être créé avant d’être ajoutée à la collection.|  
|[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)|Ajoute des données à un texte de grande taille ou les données binaires **champ**, ou à un **paramètre** objet.|  
|[BeginTrans, CommitTrans et RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)|Gère le traitement des transactions dans un **connexion** de l’objet comme suit :<br /><br /> **BeginTrans** -commence une nouvelle transaction.<br /><br /> **CommitTrans** - enregistre toutes les modifications et termine la transaction actuelle. Il peut également démarrer une nouvelle transaction.<br /><br /> **RollbackTrans** - annule toutes les modifications et termine la transaction actuelle. Il peut également démarrer une nouvelle transaction.|  
|[Annuler](../../../ado/reference/ado-api/cancel-method-ado.md)|Annule l’exécution d’une attente, l’appel de méthode asynchrone.|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Annule une mise à jour par lot en attente.|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Annule toutes les modifications qui ont été apportées à la ligne actuelle ou nouvelle d’un **Recordset** objet, ou le **champs** collection d’un **enregistrement** objet, avant d’appeler le  **Mise à jour** (méthode).|  
|[Désactiver](../../../ado/reference/ado-api/clear-method-ado.md)|Supprime tous les le **erreur** objets à partir de la **erreurs** collection.|  
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md)|Crée un doublon **Recordset** objet depuis une **Recordset** objet. Si vous le souhaitez, spécifie que le clone doit être en lecture seule.|  
|[Fermer](../../../ado/reference/ado-api/close-method-ado.md)|Ferme un objet ouvert et tous les objets dépendants.|  
|[CompareBookmarks](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)|Compare deux signets et retourne une indication de leurs valeurs relatives.|  
|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)|Copie un fichier ou répertoire et son contenu, vers un autre emplacement.|  
|[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)|Copie le nombre spécifié de caractères ou d’octets (en fonction de **Type**) dans le **Stream** vers un autre **Stream** objet.|  
|[CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)|Crée un **paramètre** objet qui possède les propriétés spécifiées.|  
|[Supprimer (Collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)|Supprime un objet à partir de la **paramètres** collection.|  
|[Supprimer (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)|Supprime un objet à partir de la **champs** collection.|  
|[Delete (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Supprime l’enregistrement actif ou un groupe d’enregistrements.|  
|[DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)|Supprime un fichier ou répertoire et tous ses sous-répertoires.|  
|[Exécuter (commande ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|Exécute la requête, une instruction SQL ou une procédure stockée spécifiée dans le **CommandText** propriété.|  
|[Exécuter (objet Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|Exécute la requête spécifiée, l’instruction SQL, le procédure stockée ou texte propre au fournisseur.|  
|[Find](../../../ado/reference/ado-api/find-method-ado.md)|Recherche un **Recordset** pour la ligne répondant aux critères spécifiés.|  
|[Flush](../../../ado/reference/ado-api/flush-method-ado.md)|Force le contenu de la **Stream** restants dans la mémoire tampon de ADO à l’objet sous-jacent auquel le **Stream** est associé.|  
|[get_OLEDBCommand, méthode](../../../ado/reference/ado-api/get-oledbcommand-method.md)|Retourne la commande OLE DB sous-jacent, tout d’abord propagation n’importe quel paramètre d’informations sur la commande ADO à la commande OLE DB.|  
|[GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)|Retourne un **Recordset** dont les lignes représentent les fichiers et sous-répertoires dans le répertoire représenté par ce **enregistrement**.|  
|[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)|Retourne l’ensemble ou une partie du contenu d’un texte de grande taille ou les données binaires **champ** objet.|  
|[GetDataProviderDSO, méthode](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Récupère l’objet de Source de données OLE DB sous-jacent à partir du fournisseur de forme.|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Récupère plusieurs enregistrements d’un **Recordset** objet dans un tableau.|  
|[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)|Retourne le **Recordset** sous forme de chaîne.|  
|[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)|Charge le contenu d’un fichier existant dans un **Stream**.|  
|[Déplacer](../../../ado/reference/ado-api/move-method-ado.md)|Déplace la position de l’enregistrement actif dans un **Recordset** objet.|  
|[MoveFirst, MoveLast, MoveNext et MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Déplace vers le premier, au dernier enregistrement suivant ou précédent dans une certaine **Recordset** objet et lui donne de l’enregistre actif.|  
|[MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md)|Déplace un fichier, ou un répertoire et son contenu, vers un autre emplacement.|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Efface actuel **Recordset** de l’objet et renvoie la prochaine **Recordset** en exécutant une série de commandes.|  
|[Open (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)|Ouvre une connexion à une source de données.|  
|[Open (objet Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|Ouvre une existante **enregistrement** de l’objet ou crée un nouveau fichier ou un répertoire.|  
|[Open (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Ouvre un curseur.|  
|[Open (Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|Ouvre un **Stream** objet à manipuler des flux de données binaires ou texte.|  
|[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)|Obtient les informations de schéma de base de données du fournisseur.|  
|[put_OLEDBCommand, méthode](../../../ado/reference/ado-api/put-oledbcommand-method.md)|Cette méthode n’effectue aucune opération - elle retourne toujours S_OK.|  
|[Lecture](../../../ado/reference/ado-api/read-method.md)|Lit un nombre spécifié d’octets à partir d’un **Stream** objet.|  
|[ReadText](../../../ado/reference/ado-api/readtext-method.md)|Lit un nombre spécifié de caractères à partir d’un texte **Stream** objet.|  
|[Actualiser](../../../ado/reference/ado-api/refresh-method-ado.md)|Met à jour les objets dans une collection afin de refléter les objets disponibles à partir d’et spécifiques au fournisseur.|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Met à jour les données dans un **Recordset** objet en exécutant à nouveau la requête sur laquelle repose l’objet.|  
|[Resync](../../../ado/reference/ado-api/resync-method.md)|Actualise les données en cours **Recordset** objet, ou **champs** collection d’un **enregistrement** objet, à partir de la base de données sous-jacente.|  
|[Enregistrer](../../../ado/reference/ado-api/save-method.md)|Enregistre le **Recordset** dans un fichier ou **Stream** objet.|  
|[SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)|Enregistre le contenu binaire d’un **Stream** dans un fichier.|  
|[Rechercher](../../../ado/reference/ado-api/seek-method.md)|Recherche l’index d’un **Recordset** pour localiser rapidement la ligne qui correspond aux valeurs spécifiées et la position de ligne actuelle pour cette ligne.|  
|[SetEOS](../../../ado/reference/ado-api/seteos-method.md)|Définit la position de la fin du flux.|  
|[SkipLine](../../../ado/reference/ado-api/skipline-method.md)|Ignore une ligne complète lors de la lecture d’un flux de texte.|  
|[Stat](../../../ado/reference/ado-api/stat-method.md)|Obtient des informations statistiques sur un flux ouvert.|  
|[Prise en charge](../../../ado/reference/ado-api/supports-method.md)|Détermine si une certaine **Recordset** objet prend en charge un type particulier de fonctionnalité.|  
|[Update](../../../ado/reference/ado-api/update-method.md)|Enregistre les modifications apportées à la ligne actuelle d’un **Recordset** objet, ou le **champs** collection d’un **enregistrement** objet.|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Écrit toutes les mises à jour par lot en attente sur le disque.|  
|[écriture](../../../ado/reference/ado-api/write-method.md)|Écrit des données binaires à un **Stream** objet.|  
|[WriteText](../../../ado/reference/ado-api/writetext-method.md)|Écrit une chaîne de texte spécifié dans un **Stream** objet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Collections ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Propriétés dynamiques ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Constantes énumérées ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Annexe B : Erreurs ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Événements ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Modèle objet ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Objets et interfaces ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Propriétés ADO](../../../ado/reference/ado-api/ado-properties.md)
