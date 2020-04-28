---
title: Correctifs logiciels Oracle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], Oraclesoftware patches
- Oracle software patches [ODBC]
ms.assetid: 1275157b-f4e1-4c24-b273-c02555e261c2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1fb577e7b08f6ef332ed35f6d275a5f7ce543ba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292949"
---
# <a name="oracle-software-patches"></a>Correctifs logiciels Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les correctifs pour les produits serveur Oracle et son composant client sont requis pour le bon fonctionnement de plusieurs produits et technologies Microsoft, notamment le pilote Microsoft ODBC pour Oracle, le Fournisseur Microsoft OLE DB pour Oracle, le Internet Information Services (IIS), les services de composants (ou Microsoft Transaction Server, si vous utilisez Windows NT), et ainsi de suite.  
  
> [!NOTE]  
>  Les instructions suivantes peuvent ne pas être entièrement précises, car le site FTP Oracle est susceptible d’être modifié.  
  
### <a name="to-download-the-oracle-software-patches"></a>Pour télécharger les correctifs logiciels Oracle  
  
1.  Connectez-vous au site FTP public sur oracle-ftp.oracle.com. L’ID d’utilisateur est « Anonymous » et le mot de passe est votre adresse de messagerie.  
  
2.  Accédez au répertoire suivant:/Server/wgt_tech/server/windowsNT.  
  
3.  Pour télécharger les correctifs les plus pertinents pour Windows 95, Windows 98 et Windows NT/Windows 2000, accédez au sous-répertoire de votre version d’Oracle-7,3 ou 8,0. Les deux sous-répertoires sont/73patchsets et/80patchsets.  
  
4.  Pour télécharger des correctifs pour la technologie réseau Oracle, SQL * NET ou Net8, accédez au répertoire suivant:/Network.  
  
 L’accès à ce site FTP à partir de votre navigateur Web peut ne pas fonctionner. Si vous rencontrez des problèmes, essayez d’utiliser un client FTP « traditionnel » ou utilisez l’invite de commandes DOS.  
  
> [!NOTE]  
>  Étant donné qu’Oracle corrige les bogues dans les versions actuelles et les distribue aux versions antérieures à l’aide de correctifs logiciels, il est recommandé de télécharger le correctif le plus récent disponible. Cela est particulièrement vrai pour les composants client Oracle Server. Si vous avez des questions sur l’installation de ces correctifs, contactez le support Oracle.
