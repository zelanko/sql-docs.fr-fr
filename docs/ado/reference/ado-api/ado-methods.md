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
author: rothja
ms.author: jroth
ms.openlocfilehash: 65145ce8f77c352fb24a2a206d99828298b6a60c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747255"
---
# <a name="ado-methods"></a>Méthodes ADO

|||  
|-|-|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Crée un nouvel enregistrement pour un objet **Recordset** pouvant être mis à jour.|  
|[Append](../../../ado/reference/ado-api/append-method-ado.md)|Ajoute un objet à une collection. Si la collection est de **champs**, un nouvel objet de **champ** peut être créé avant d’être ajouté à la collection.|  
|[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)|Ajoute des données à un **champ**de données de texte ou binaires volumineux, ou à un objet de **paramètre** .|  
|[BeginTrans, CommitTrans et RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)|Gère le traitement des transactions dans un objet de **connexion** comme suit :<br /><br /> **BeginTrans** -commence une nouvelle transaction.<br /><br /> **CommitTrans** : enregistre les modifications et met fin à la transaction en cours. Elle peut également démarrer une nouvelle transaction.<br /><br /> **RollbackTrans** -annule toutes les modifications et met fin à la transaction en cours. Elle peut également démarrer une nouvelle transaction.|  
|[Annuler](../../../ado/reference/ado-api/cancel-method-ado.md)|Annule l’exécution d’un appel de méthode asynchrone en attente.|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Annule une mise à jour par lot en attente.|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Annule toutes les modifications apportées à la ligne actuelle ou nouvelle d’un objet **Recordset** , ou à la collection **Fields** d’un objet **Record** , avant d’appeler la méthode **Update** .|  
|[Effacer](../../../ado/reference/ado-api/clear-method-ado.md)|Supprime tous les objets **Error** de la collection **Errors** .|  
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md)|Crée un objet **Recordset** dupliqué à partir d’un objet **Recordset** existant. Spécifie éventuellement que le clone doit être en lecture seule.|  
|[Close](../../../ado/reference/ado-api/close-method-ado.md)|Ferme un objet ouvert et tous les objets dépendants.|  
|[CompareBookmarks,](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)|Compare deux signets et retourne une indication de leurs valeurs relatives.|  
|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)|Copie un fichier ou un répertoire, ainsi que son contenu, vers un autre emplacement.|  
|[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)|Copie le nombre spécifié de caractères ou d’octets (selon le **type**) dans le **flux** vers un autre objet de **flux** .|  
|[CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)|Crée un objet de **paramètre** qui a les propriétés spécifiées.|  
|[Delete (collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)|Supprime un objet de la collection de **paramètres** .|  
|[Delete (collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)|Supprime un objet de la collection de **champs** .|  
|[Delete (Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Supprime l’enregistrement en cours ou un groupe d’enregistrements.|  
|[DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)|Supprime un fichier ou un répertoire, ainsi que tous ses sous-répertoires.|  
|[Execute (commande ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|Exécute la requête, l’instruction SQL ou la procédure stockée spécifiée dans la propriété **CommandText** .|  
|[Execute (connexion ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|Exécute la requête, l’instruction SQL, la procédure stockée ou le texte spécifique au fournisseur spécifié.|  
|[Rechercher](../../../ado/reference/ado-api/find-method-ado.md)|Recherche dans un **Recordset** la ligne qui répond aux critères spécifiés.|  
|[Postconsommation](../../../ado/reference/ado-api/flush-method-ado.md)|Force le contenu du **flux** restant dans la mémoire tampon ADO à l’objet sous-jacent auquel le **flux** est associé.|  
|[get_OLEDBCommand, méthode](../../../ado/reference/ado-api/get-oledbcommand-method.md)|Retourne la commande OLEDB sous-jacente, en propageant tout d’abord les informations sur les paramètres définis sur la commande ADO à la commande OLEDB.|  
|[GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)|Retourne un **jeu d’enregistrements** dont les lignes représentent les fichiers et les sous-répertoires du répertoire représenté par cet **enregistrement**.|  
|[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)|Retourne l’intégralité ou une partie du contenu d’un objet de texte ou de **champ** de données binaire volumineux.|  
|[GetDataProviderDSO, méthode](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Récupère l’objet source de données OLEDB sous-jacent à partir du fournisseur de formes.|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Récupère plusieurs enregistrements d’un objet **Recordset** dans un tableau.|  
|[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)|Retourne le **Recordset** sous forme de chaîne.|  
|[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)|Charge le contenu d’un fichier existant dans un **flux**.|  
|[Déplacer](../../../ado/reference/ado-api/move-method-ado.md)|Déplace la position de l’enregistrement actuel dans un objet **Recordset** .|  
|[MoveFirst, MoveLast, MoveNext et MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Passe au premier enregistrement, dernier, suivant ou précédent dans un objet **Recordset** spécifié et convertit cet enregistrement en enregistrement actif.|  
|[MoveRecord,](../../../ado/reference/ado-api/moverecord-method-ado.md)|Déplace un fichier, ou un répertoire et son contenu, vers un autre emplacement.|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Efface l’objet **Recordset** actuel et retourne le **jeu d’enregistrements** suivant en progressant dans une série de commandes.|  
|[Open (connexion ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)|Ouvre une connexion à une source de données.|  
|[Open (enregistrement ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|Ouvre un objet **enregistrement** existant ou crée un fichier ou un répertoire.|  
|[Open (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Ouvre un curseur.|  
|[Open (objet Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|Ouvre un objet de **flux** pour manipuler des flux de données binaires ou de texte.|  
|[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)|Obtient des informations de schéma de base de données à partir du fournisseur.|  
|[put_OLEDBCommand, méthode](../../../ado/reference/ado-api/put-oledbcommand-method.md)|Cette méthode n’effectue aucune opération. elle retourne toujours S_OK.|  
|[Lecture](../../../ado/reference/ado-api/read-method.md)|Lit un nombre spécifié d’octets à partir d’un objet de **flux** .|  
|[ReadText](../../../ado/reference/ado-api/readtext-method.md)|Lit un nombre spécifié de caractères à partir d’un objet de **flux** de texte.|  
|[Actualisation](../../../ado/reference/ado-api/refresh-method-ado.md)|Met à jour les objets d’une collection pour refléter les objets disponibles et spécifiques au fournisseur.|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Met à jour les données dans un objet **Recordset** en exécutant à nouveau la requête sur laquelle l’objet est basé.|  
|[Resynchroniser](../../../ado/reference/ado-api/resync-method.md)|Actualise les données de la base de données sous-jacente de l’objet **Recordset** actuel ou de la collection **Fields** d’un objet **Record** .|  
|[Save](../../../ado/reference/ado-api/save-method.md)|Enregistre le **Recordset** dans un objet de fichier ou de **flux** .|  
|[SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)|Enregistre le contenu binaire d’un **flux** dans un fichier.|  
|[Seek](../../../ado/reference/ado-api/seek-method.md)|Recherche l’index d’un **jeu d’enregistrements** pour localiser rapidement la ligne qui correspond aux valeurs spécifiées et modifie la position de ligne actuelle en cette ligne.|  
|[SetEOS](../../../ado/reference/ado-api/seteos-method.md)|Définit la position qui correspond à la fin du flux.|  
|[SkipLine](../../../ado/reference/ado-api/skipline-method.md)|Ignore une ligne entière lors de la lecture d’un flux de texte.|  
|[Stat](../../../ado/reference/ado-api/stat-method.md)|Obtient des informations statistiques sur un flux ouvert.|  
|[Permet](../../../ado/reference/ado-api/supports-method.md)|Détermine si un objet **Recordset** spécifié prend en charge un type particulier de fonctionnalité.|  
|[Mettre à jour](../../../ado/reference/ado-api/update-method.md)|Enregistre les modifications apportées à la ligne actuelle d’un objet **Recordset** ou à la collection **Fields** d’un objet **Record** .|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Écrit toutes les mises à jour par lots en attente sur le disque.|  
|[Écriture](../../../ado/reference/ado-api/write-method.md)|Écrit des données binaires dans un objet de **flux** .|  
|[WriteText](../../../ado/reference/ado-api/writetext-method.md)|Écrit une chaîne de texte spécifiée dans un objet de **flux** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Collections ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Propriétés dynamiques ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Constantes énumérées ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Annexe B : erreurs ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Événements ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Modèle objet ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Objets et interfaces ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Propriétés ADO](../../../ado/reference/ado-api/ado-properties.md)
