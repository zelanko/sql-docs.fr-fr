---
title: ErrorValueEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ErrorValueEnum
helpviewer_keywords:
- ErrorValueEnum enumeration [ADO]
ms.assetid: 9469ba3a-5e4f-4a10-bbb8-a51a6c9660ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18117be8dccc64f7ed2583170cf062145836f337
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932872"
---
# <a name="errorvalueenum"></a>ErrorValueEnum
Spécifie le type d’erreur d’exécution ADO.  
  
 Trois formes de numéro d’erreur sont répertoriés :  
  
-   Positif décimale, à savoir le deux octets faibles du nombre complet au format décimal. Ce nombre est affiché dans la boîte de dialogue de message par défaut Visual Basic erreur. Par exemple, erreur d’exécution '3707 ''.  
  
-   La valeur décimale-la conversion décimale du numéro d’erreur complet.  
  
-   Représentation hexadécimale hexadécimal, à savoir le du numéro d’erreur complet. Le code de fonction Windows est dans le quatrième chiffre. Le code de fonction des numéros d’erreur ADO est *A*. Exemple : 0 x 800***A***0E7B.  
  
> [!NOTE]
>  Erreurs OLE DB peuvent être passés à votre application ADO. En règle générale, elles peuvent être identifiées par un code de fonction Windows *4*. Par exemple, 0 x 800***4***.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adErrBoundToCommand**|3707-2146824581 0x800A0E7B|Ne peut pas modifier le **ActiveConnection** propriété d’un **Recordset** objet qui a un **commande** objet en tant que sa source.|  
|**adErrCannotComplete**|3732 -2146824556 0x800A0E94|Serveur ne peut pas terminer l’opération.|  
|**adErrCantChangeConnection**|3748 -2146824540 0x800A0EA4|Connexion a été refusée. Nouvelle connexion que vous avez demandée a des caractéristiques différentes de celles celui déjà utilisé.|  
|**adErrCantChangeProvider**|3220 -2146825068 0X800A0C94|Le fournisseur indiqué diffère de celui déjà utilisé.|  
|**adErrCantConvertvalue**|3724-2146824564 0x800A0E8C|Valeur de données ne peut pas être convertie pour des raisons autres que l’authentification incompatibilité ou données de dépassement. Par exemple, conversion aurait tronqué les données.|  
|**adErrCantCreate**|3725-2146824563 0x800A0E8D|Valeur de données ne peut pas être définie ou récupérée, car le type de données de champ est inconnu, ou le fournisseur a des ressources insuffisantes pour effectuer l’opération.|  
|**adErrCatalogNotSet**|3747 -2146824541 0x800A0EA3|Opération nécessite une valide **ParentCatalog**.|  
|**adErrColumnNotOnThisRow**|3726 -2146824562 0x800A0E8E|Enregistrement ne contient pas ce champ.|  
|**adErrDataConversion**|3421-2146824867 0x800A0D5D|Application utilise une valeur de type incorrect pour l’opération actuelle.|  
|**adErrDataOverflow**|3721 -2146824567 0x800A0E89|Valeur de données est trop grande pour être représentée par le type de données de champ.|  
|**adErrDelResOutOfScope**|3738-2146824550 0x800A0E9A|URL de l’objet à supprimer est en dehors de l’étendue de l’enregistrement en cours.|  
|**adErrDenyNotSupported**|3750 -2146824538 0x800A0EA6|Fournisseur ne prend pas en charge les restrictions de partage.|  
|**adErrDenyTypeNotSupported**|3751 -2146824537 0x800A0EA7|Fournisseur ne prend pas en charge le type demandé de restriction de partage.|  
|**adErrFeatureNotAvailable**|3251 -2146825037 0x800A0CB3|Objet ou le fournisseur n’est pas en mesure d’effectuer l’opération demandée.|  
|**adErrFieldsUpdateFailed**|3749 -2146824539 0x800A0EA5|Échec de la mise à jour des champs. Pour plus d’informations, examinez la **état** des propriétés des objets de champ individuel.|  
|**adErrIllegalOperation**|3219 -2146825069 0x800A0C93|Opération n’est pas autorisée dans ce contexte.|  
|**adErrIntegrityViolation**|3719 -2146824569 0x800A0E87|Valeur de données est en conflit avec les contraintes d’intégrité du champ.|  
|**adErrInTransaction**|3246-2146825042 0x800A0CAE|**Connexion** objet ne peut pas être explicitement fermé pendant une transaction.|  
|**adErrInvalidArgument**|3001 -2146825287 0x800A0BB9|Arguments sont de type incorrect, sont hors des limites autorisées ou sont en conflit avec eux.|  
|**adErrInvalidConnection**|3709 -2146824579 0x800A0E7D|La connexion ne peut pas être utilisée pour effectuer cette opération. Il est fermé ou non valide dans ce contexte.|  
|**adErrInvalidParamInfo**|3708 -2146824580 0x800A0E7C|**Paramètre** objet est défini de manière incorrecte. Informations incohérentes ou incomplets ont été fournies.|  
|**adErrInvalidTransaction**|3714 -2146824574 0x800A0E82|Coordination de transaction n’est pas valide ou n’a pas démarré.|  
|**adErrInvalidURL**|3729 -2146824559 0x800A0E91|URL contient des caractères non valides. Assurez-vous que l’URL est correcte.|  
|**adErrItemNotFound**|3265-2146825023 0x800A0CC1|Élément est introuvable dans la collection qui correspond au nom demandé ou ordinales.|  
|**adErrNoCurrentRecord**|3021 -2146825267 0x800A0BCD|Soit **BOF** ou **EOF** a la valeur True, ou l’enregistrement en cours a été supprimé. Opération demandée nécessite un enregistrement actuel.|  
|**adErrNotExecuting**|3715 -2146824573 0x800A0E83|Impossible d’effectuer l’opération lors de la non-exécution.|  
|**adErrNotReentrant**|3710 -2146824578 0x800A0E7E|Impossible d’effectuer l’opération pendant le traitement de l’événement.|  
|**adErrObjectClosed**|3704 -2146824584 0x800A0E78|Opération n’est pas autorisée lorsque l’objet est fermé.|  
|**adErrObjectInCollection**|3367-2146824921 0x800A0D27|Objet est déjà dans la collection. Impossible d’ajouter.|  
|**adErrObjectNotSet**|3420 -2146824868 0x800A0D5C|Objet n’est plus valide.|  
|**adErrObjectOpen**|3705 -2146824583 0x800A0E79|Opération n’est pas autorisée lorsque l’objet est ouvert.|  
|**adErrOpeningFile**|3002 -2146825286 0x800A0BBA|Fichier n’a pas pu être ouvert.|  
|**adErrOperationCancelled**|3712 -2146824576 0x800A0E80|A été annulée par l’utilisateur.|  
|**adErrOutOfSpace**|3734 -2146824554 0x800A0E96|Impossible d’effectuer l’opération. Le fournisseur ne peut pas obtenir suffisamment d’espace libre.|  
|**adErrPermissionDenied**|3720 -2146824568 0x800A0E88|Autorisation insuffisante empêche l’écriture dans le champ.|  
|**adErrProviderFailed**|3000 -2146825288 0x800A0BB8|Fournisseur n’a pas effectué l’opération demandée.|  
|**adErrProviderNotFound**|3706 -2146824582 0x800A0E7A|Impossible de trouver un fournisseur. Il ne peut pas être correctement installé.|  
|**adErrReadFile**|3003-2146825285 0x800A0BBB|Fichier n’a pas pu être lu.|  
|**adErrResourceExists**|3731 -2146824557 0x800A0E93|Opération de copie ne peut pas être effectuée. Objet nommé par l’URL de destination existe déjà. Spécifiez **adCopyOverwrite** remplacer l’objet.|  
|**adErrResourceLocked**|3730 -2146824558 0x800A0E92|Objet représenté par l’URL spécifiée est verrouillé par un ou plusieurs processus. Attendez que le processus est terminé et recommencez l’opération.|  
|**adErrResourceOutOfScope**|3735 -2146824553 0x800A0E97|URL source ou de destination est en dehors de l’étendue de l’enregistrement en cours.|  
|**adErrSchemaViolation**|3722 -2146824566 0x800A0E8A|Valeur de données est en conflit avec le type de données ou les contraintes du champ.|  
|**adErrSignMismatch**|3723-2146824565 0x800A0E8B|Conversion a échoué car la valeur de données était signée et le type de données utilisé par le fournisseur n’était pas signé.|  
|**adErrStillConnecting**|3713 -2146824575 0x800A0E81|Impossible d’effectuer l’opération lors de la connexion de façon asynchrone.|  
|**adErrStillExecuting**|3711 -2146824577 0x800A0E7F|Impossible d’effectuer l’opération lors de l’exécution de façon asynchrone.|  
|**adErrTreePermissionDenied**|3728 -2146824560 0x800A0E90|Les autorisations sont insuffisantes pour accéder à l’arborescence ou une sous-arborescence.|  
|**adErrUnavailable**|3736 -2146824552 0x800A0E98|Impossible d’achever et l’état n’est pas disponible. Le champ est peut-être indisponible ou l’opération a été tentée pas.|  
|**adErrUnsafeOperation**|3716 -2146824572 0x800A0E84|Paramètres de sécurité de cet ordinateur empêchent l’accès à une source de données sur un autre domaine.|  
|**adErrURLDoesNotExist**|3727-2146824561 0x800A0E8F|L’URL source ou le parent de l’URL de destination n’existe pas.|  
|**adErrURLNamedRowDoesNotExist**|3737 -2146824551 0x800A0E99|Enregistrement portant ce nom n’existe pas.|  
|**adErrVolumeNotFound**|3733 -2146824555 0x800A0E95|Fournisseur ne peut pas localiser le périphérique de stockage indiqué par l’URL. Assurez-vous que l’URL est correcte.|  
|**adErrWriteFile**|3004 -2146825284 0x800A0BBC|Écriture dans le fichier a échoué.|  
|**adWrnSecurityDialog**|3717 -2146824571 0x800A0E85|À usage interne uniquement. Ne pas utiliser.|  
|**adWrnSecurityDialogHeader**|3718 -2146824570 0x800A0E86|À usage interne uniquement. Ne pas utiliser.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Package : **com.ms.wfc.data**  
  
 Seuls les sous-ensembles suivants d’équivalents ADO/WFC sont définis.  
  
|Constante|  
|--------------|  
|AdoEnums.ErrorValue.BOUNDTOCOMMAND|  
|AdoEnums.ErrorValue.DATACONVERSION|  
|AdoEnums.ErrorValue.FEATURENOTAVAILABLE|  
|AdoEnums.ErrorValue.ILLEGALOPERATION|  
|AdoEnums.ErrorValue.INTRANSACTION|  
|AdoEnums.ErrorValue.INVALIDARGUMENT|  
|AdoEnums.ErrorValue.INVALIDCONNECTION|  
|AdoEnums.ErrorValue.INVALIDPARAMINFO|  
|AdoEnums.ErrorValue.ITEMNOTFOUND|  
|AdoEnums.ErrorValue.NOCURRENTRECORD|  
|AdoEnums.ErrorValue.NOTEXECUTING|  
|AdoEnums.ErrorValue.NOTREENTRANT|  
|AdoEnums.ErrorValue.OBJECTCLOSED|  
|AdoEnums.ErrorValue.OBJECTINCOLLECTION|  
|AdoEnums.ErrorValue.OBJECTNOTSET|  
|AdoEnums.ErrorValue.OBJECTOPEN|  
|AdoEnums.ErrorValue.OPERATIONCANCELLED|  
|AdoEnums.ErrorValue.PROVIDERNOTFOUND|  
|AdoEnums.ErrorValue.STILLCONNECTING|  
|AdoEnums.ErrorValue.STILLEXECUTING|  
|AdoEnums.ErrorValue.UNSAFEOPERATION|  
  
## <a name="applies-to"></a>S'applique à  
 [Number, propriété (ADO)](../../../ado/reference/ado-api/number-property-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Codes d’erreur ADO](../../../ado/guide/appendixes/ado-error-codes.md)
