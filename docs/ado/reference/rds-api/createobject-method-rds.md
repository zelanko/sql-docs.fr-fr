---
title: CreateObject, méthode (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6b50714cdff536418e759828d972c16abd7d7a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964544"
---
# <a name="createobject-method-rds"></a>CreateObject, méthode (RDS)
Crée le proxy pour l’objet métier cible et retourne un pointeur vers celui-ci. Le proxy conditionne et marshale les données vers le stub côté serveur pour les communications avec l’objet métier pour envoyer des requêtes et des données sur Internet. Pour les objets de composant in-process, aucun proxy n’est utilisé, mais simplement un pointeur vers l’objet est fourni.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
 Remote Data Service prend en charge les protocoles suivants : HTTP, HTTPs (HTTP sur SSL), DCOM et in-process.  
  
|Protocol|Syntaxe|  
|--------------|------------|  
|HTTP|Set Object = DataSpace. CreateObject ("ProgId", "https\://awebsrvr")|  
|HTTPS|Set Object = DataSpace. CreateObject ("ProgId", "https\://awebsrvr")|  
|DCOM|Set Object = DataSpace. CreateObject ("ProgId", "ComputerName")|  
|In-process|Set Object = DataSpace. CreateObject ("ProgId", "")|  
  
## <a name="parameters"></a>Paramètres  
 *Object*  
 Variable objet qui prend la valeur d’un objet qui est le type spécifié dans *ProgID*.  
  
 *DataSpace*  
 Variable objet qui représente un objet [RDS. Objet DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) utilisé pour créer une instance du nouvel objet.  
  
 *ProgID*  
 Valeur de **chaîne** qui contient l’identificateur programmatique spécifiant un objet métier côté serveur qui implémente les règles métier de votre application.  
  
 *awebsrvr* ou *ComputerName*  
 Valeur de **chaîne** qui représente une URL identifiant le serveur Web Internet Information Services (IIS) sur lequel une instance de l’objet métier serveur est créée.  
  
## <a name="remarks"></a>Notes  
 Le *protocole http* est le protocole Web standard. *Https* est un protocole Web sécurisé. Utilisez le *protocole DCOM* lors de l’exécution d’un réseau local sans http. Le protocole *in-process* est une bibliothèque de liens dynamiques (dll) locale ; Il n’utilise pas de réseau.  
  
## <a name="applies-to"></a>S'applique à  
 [DataSpace, objet (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet DataFactory, méthode Query et CreateObject, exemple de méthode (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [DataSpace, exemple d’objet et CreateObject, exemple de méthode (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [CreateRecordset, méthode (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


