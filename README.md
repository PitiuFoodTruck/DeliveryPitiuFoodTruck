<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="HandheldFriendly" content="true">
  <meta name="MobileOptimized" content="width">
  <meta name="theme-color" content="#d35400">
  <meta name="format-detection" content="telephone=no">
  <title>Cardápio Completo - FoodTruck do Pitiu</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  
  <style>
    :root {
      --primary-color: #d35400;
      --secondary-color: #e67e22;
      --dark-color: #222;
      --light-color: #f9f9f9;
      --success-color: #27ae60;
      --danger-color: #e74c3c;
      --info-color: #3498db;
      --open-color: #2ecc71;
      --closed-color: #e74c3c;
      --salty-section: rgba(52, 152, 219, 0.1);
      --sweet-section: rgba(231, 76, 60, 0.1);
    }
    
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
      -webkit-text-size-adjust: 100%;
      -ms-text-size-adjust: 100%;
    }
    
    html {
      width: 100%;
      overflow-x: hidden;
      -webkit-overflow-scrolling: touch;
    }
    
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
      color: #333;
      line-height: 1.6;
      background-image: url('backgroundfoodtruckpitiu.png');
      background-size: cover;
      background-attachment: fixed;
      background-position: center;
      background-color: rgba(0, 0, 0, 0.2);
      background-blend-mode: soft-light;
      touch-action: manipulation;
      width: 100%;
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
    }
    
    body::before {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.2);
      z-index: -1;
    }

    /* Botão de voltar ao topo */
    .back-to-top {
      position: fixed;
      bottom: 80px;
      right: 20px;
      width: 50px;
      height: 50px;
      background-color: red;
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      cursor: pointer;
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s ease;
      z-index: 99;
    }

    .back-to-top.show {
      opacity: 1;
      visibility: visible;
    }

    .back-to-top:hover {
      background-color: #c0392b;
    }
    
    .header {
      background-color: rgba(34, 34, 34, 0.9);
      color: white;
      text-align: center;
      padding: 1rem 0.5rem;
      position: relative;
      border-bottom: 3px solid var(--primary-color);
      width: 100%;
      max-width: 100%;
    }
    
    .logo {
      max-width: 120px;
      margin-bottom: 0.5rem;
      height: auto;
    }
    
    .header h1 {
      font-size: 1.5rem;
      margin-bottom: 0.5rem;
      color: var(--secondary-color);
      word-wrap: break-word;
      padding: 0 5px;
    }
    
    .header p {
      font-size: 0.8rem;
      margin-bottom: 0.3rem;
      padding: 0 5px;
      word-wrap: break-word;
    }
    
    .status {
      display: inline-block;
      padding: 0.3rem 0.6rem;
      border-radius: 20px;
      font-weight: bold;
      margin: 0.3rem 0;
      font-size: 0.8rem;
    }
    
    .status.open {
      background-color: var(--open-color);
      color: white;
    }
    
    .status.closed {
      background-color: var(--closed-color);
      color: white;
    }
    
    .header .social-links {
      margin-top: 0.5rem;
    }
    
    .header .social-links a {
      color: white;
      margin: 0 8px;
      font-size: 1.1rem;
      transition: color 0.3s;
    }
    
    .header .social-links a:hover {
      color: var(--secondary-color);
    }
    
    .tabs {
      display: flex;
      justify-content: flex-start;
      background-color: rgba(34, 34, 34, 0.95);
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      overflow-x: auto;
      white-space: nowrap;
      padding: 0.3rem 0;
      -webkit-overflow-scrolling: touch;
      width: 100%;
      max-width: 100%;
      scrollbar-width: none; /* Firefox */
    }
    
    .tabs::-webkit-scrollbar {
      display: none; /* Chrome, Safari, Opera */
    }
    
    .tab-button {
      padding: 0.6rem 0.8rem;
      color: white;
      text-decoration: none;
      font-weight: bold;
      text-transform: uppercase;
      letter-spacing: 1px;
      transition: all 0.3s;
      cursor: pointer;
      border-bottom: 3px solid transparent;
      font-size: 0.7rem;
      touch-action: manipulation;
      flex-shrink: 0;
    }
    
    .tab-button:hover, .tab-button:active {
      background-color: rgba(255,255,255,0.1);
      border-bottom: 3px solid var(--secondary-color);
    }
    
    .tab-button.active {
      background-color: rgba(255,255,255,0.1);
      border-bottom: 3px solid var(--primary-color);
    }
    
    .container {
      display: flex;
      flex-direction: column;
      max-width: 100%;
      margin: 0 auto;
      padding: 0.8rem;
      width: 100%;
      box-sizing: border-box;
      position: relative;
      padding-bottom: 80px;
    }
    
    .menu-section {
      width: 100%;
      margin-bottom: 1rem;
    }
    
    .cart-section {
      width: 100%;
      background-color: rgba(255, 255, 255, 0.95);
      border-radius: 8px;
      box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
      padding: 0.8rem;
      z-index: 90;
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      box-sizing: border-box;
      max-height: 40vh;
      overflow-y: auto;
      transform: translateY(0);
      transition: transform 0.3s ease;
    }
    
    .cart-section.hidden {
      transform: translateY(100%);
    }
    
    .category {
      margin-bottom: 1.5rem;
      background-color: rgba(255, 255, 255, 0.95);
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      width: 100%;
      box-sizing: border-box;
    }
    
    .category-header {
      background-color: var(--primary-color);
      color: white;
      padding: 0.7rem 0.8rem;
      font-size: 1.1rem;
      position: relative;
    }
    
    .category-header::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 3px;
      background-color: var(--secondary-color);
    }
    
    .item {
      display: flex;
      flex-direction: column;
      padding: 0.8rem;
      border-bottom: 1px solid #eee;
      transition: background-color 0.3s;
      width: 100%;
      box-sizing: border-box;
    }
    
    .item:last-child {
      border-bottom: none;
    }
    
    .item:hover {
      background-color: rgba(0,0,0,0.03);
    }
    
    .item-image {
      width: 100%;
      height: 150px;
      object-fit: cover;
      border-radius: 8px;
      margin-bottom: 0.8rem;
      cursor: pointer;
    }
    
    .item-details {
      width: 100%;
    }
    
    .item-title {
      font-size: 1rem;
      font-weight: bold;
      margin-bottom: 0.3rem;
      color: var(--dark-color);
      word-wrap: break-word;
    }
    
    .item-description {
      font-size: 0.85rem;
      color: #666;
      margin-bottom: 0.5rem;
      word-wrap: break-word;
    }
    
    .item-price {
      font-weight: bold;
      color: var(--primary-color);
      font-size: 1rem;
    }
    
    .item-actions {
      display: flex;
      align-items: center;
      margin-top: 0.5rem;
      width: 100%;
    }
    
    .add-to-cart {
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 0.5rem 0.8rem;
      border-radius: 4px;
      cursor: pointer;
      font-weight: bold;
      transition: background-color 0.3s;
      touch-action: manipulation;
      width: 100%;
      font-size: 0.9rem;
    }
    
    .add-to-cart:hover, .add-to-cart:active {
      background-color: var(--secondary-color);
    }
    
    .cart-title {
      font-size: 1.2rem;
      margin-bottom: 0.8rem;
      padding-bottom: 0.5rem;
      border-bottom: 2px solid var(--primary-color);
      color: var(--dark-color);
    }
    
    .cart-items {
      margin-bottom: 0.8rem;
      max-height: 150px;
      overflow-y: auto;
      -webkit-overflow-scrolling: touch;
      width: 100%;
    }
    
    .cart-item {
      display: flex;
      flex-direction: column;
      padding: 0.5rem 0;
      border-bottom: 1px solid #eee;
      width: 100%;
    }
    
    .cart-item-row {
      display: flex;
      justify-content: space-between;
      width: 100%;
    }
    
    .cart-item-name {
      flex: 2;
      font-size: 0.9rem;
      word-break: break-word;
    }
    
    .cart-item-price {
      flex: 1;
      text-align: right;
      font-size: 0.9rem;
    }
    
    .cart-item-remove {
      color: var(--danger-color);
      margin-left: 0.5rem;
      cursor: pointer;
      background: none;
      border: none;
      font-size: 0.8rem;
    }
    
    .cart-item-quantity {
      display: flex;
      align-items: center;
      margin-top: 0.3rem;
      width: 100%;
      justify-content: flex-start;
    }
    
    .quantity-btn {
      background-color: #f0f0f0;
      border: none;
      width: 25px;
      height: 25px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      font-weight: bold;
      font-size: 0.9rem;
    }
    
    .quantity-value {
      margin: 0 0.5rem;
      min-width: 20px;
      text-align: center;
      font-size: 0.9rem;
    }
    
    .cart-item-notes {
      width: 100%;
      font-size: 0.75rem;
      color: #666;
      margin-top: 0.3rem;
      font-style: italic;
      word-break: break-word;
    }
    
    .cart-total {
      font-weight: bold;
      font-size: 1.1rem;
      margin-top: 0.8rem;
      padding-top: 0.8rem;
      border-top: 2px solid var(--primary-color);
      text-align: right;
    }
    
    .cart-actions {
      margin-top: 1rem;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
    }
    
    .cart-button {
      width: 100%;
      padding: 0.7rem;
      border: none;
      border-radius: 4px;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s;
      touch-action: manipulation;
      font-size: 0.9rem;
    }
    
    .checkout-button {
      background-color: var(--success-color);
      color: white;
    }
    
    .checkout-button:hover, .checkout-button:active {
      background-color: #2ecc71;
    }
    
    .clear-button {
      background-color: var(--danger-color);
      color: white;
    }
    
    .clear-button:hover, .clear-button:active {
      background-color: #c0392b;
    }
    
    .preview-button {
      background-color: var(--info-color);
      color: white;
    }
    
    .preview-button:hover, .preview-button:active {
      background-color: #2980b9;
    }
    
    .empty-cart {
      text-align: center;
      color: #666;
      padding: 0.8rem 0;
      font-size: 0.9rem;
    }
    
    /* Modal de Checkout */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.7);
      z-index: 1000;
      overflow-y: auto;
      -webkit-overflow-scrolling: touch;
    }
    
    .modal-content {
      background-color: white;
      margin: 1.5rem auto;
      padding: 1.2rem;
      border-radius: 8px;
      max-width: 95%;
      width: 100%;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      box-sizing: border-box;
    }
    
    .close-modal {
      float: right;
      font-size: 1.3rem;
      cursor: pointer;
      color: #666;
    }
    
    .form-group {
      margin-bottom: 0.8rem;
      width: 100%;
    }
    
    .form-group label {
      display: block;
      margin-bottom: 0.4rem;
      font-weight: bold;
      font-size: 0.9rem;
    }
    
    .form-group input, 
    .form-group select, 
    .form-group textarea {
      width: 100%;
      padding: 0.7rem;
      border: 1px solid #ddd;
      border-radius: 4px;
      font-family: inherit;
      font-size: 0.9rem;
      box-sizing: border-box;
    }
    
    .form-group textarea {
      min-height: 80px;
    }
    
    .delivery-fee {
      padding: 0.8rem;
      background-color: #f5f5f5;
      border-radius: 4px;
      margin: 0.8rem 0;
      font-weight: bold;
      font-size: 0.9rem;
    }
    
    .order-summary {
      margin: 0.8rem 0;
      padding: 0.8rem;
      background-color: #f9f9f9;
      border-radius: 4px;
      font-size: 0.9rem;
    }
    
    .order-item {
      display: flex;
      justify-content: space-between;
      margin-bottom: 0.4rem;
      font-size: 0.9rem;
    }
    
    .order-total {
      font-weight: bold;
      font-size: 1.1rem;
      margin-top: 0.8rem;
      border-top: 1px solid #ddd;
      padding-top: 0.8rem;
    }
    
    .payment-options {
      margin: 0.8rem 0;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      width: 100%;
    }
    
    .payment-option {
      margin-bottom: 0.5rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      min-width: 100px;
      position: relative;
    }
    
    .payment-option input {
      margin-right: 0.5rem;
      flex-shrink: 0;
    }
    
    .payment-option label {
      font-size: 0.9rem;
      word-break: break-word;
      text-align: center;
      margin-top: 5px;
    }
    
    .payment-dot {
      width: 10px;
      height: 10px;
      background-color: var(--primary-color);
      border-radius: 50%;
      position: absolute;
      bottom: -15px;
      left: 50%;
      transform: translateX(-50%);
      opacity: 0;
      transition: opacity 0.3s;
    }
    
    .payment-option input:checked ~ .payment-dot {
      opacity: 1;
    }
    
    .submit-order {
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 0.9rem;
      border-radius: 4px;
      font-weight: bold;
      cursor: pointer;
      width: 100%;
      font-size: 1rem;
      transition: background-color 0.3s;
      margin-top: 0.5rem;
    }
    
    .submit-order:hover, .submit-order:active {
      background-color: var(--secondary-color);
    }
    
    /* Modal de Observação */
    .notes-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.7);
      z-index: 1001;
      overflow-y: auto;
      -webkit-overflow-scrolling: touch;
    }
    
    .notes-content {
      background-color: white;
      margin: 1.5rem auto;
      padding: 1.2rem;
      border-radius: 8px;
      max-width: 95%;
      width: 100%;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      box-sizing: border-box;
    }
    
    .notes-actions {
      display: flex;
      justify-content: space-between;
      margin-top: 1rem;
      width: 100%;
      gap: 0.5rem;
    }
    
    .notes-actions button {
      flex: 1;
      padding: 0.7rem;
      font-size: 0.9rem;
    }
    
    /* Modal de Visualização do Item */
    .item-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.7);
      z-index: 1002;
      overflow-y: auto;
      -webkit-overflow-scrolling: touch;
    }
    
    .item-modal-content {
      background-color: white;
      margin: 1.5rem auto;
      padding: 1.2rem;
      border-radius: 8px;
      max-width: 95%;
      width: 100%;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      text-align: center;
      box-sizing: border-box;
    }
    
    .item-modal-image {
      max-width: 100%;
      height: auto;
      max-height: 250px;
      object-fit: cover;
      border-radius: 8px;
      margin-bottom: 1rem;
    }
    
    .item-modal-title {
      font-size: 1.2rem;
      color: var(--primary-color);
      margin-bottom: 0.5rem;
      word-break: break-word;
    }
    
    .item-modal-description {
      color: #666;
      margin-bottom: 1rem;
      font-size: 0.9rem;
      word-break: break-word;
    }
    
    /* Opções de retirada */
    .delivery-options {
      display: flex;
      flex-direction: column;
      margin-bottom: 0.8rem;
      border: 1px solid #ddd;
      border-radius: 4px;
      overflow: hidden;
      width: 100%;
    }
    
    .delivery-option {
      text-align: center;
      padding: 0.7rem;
      cursor: pointer;
      transition: all 0.3s;
      border-bottom: 1px solid #ddd;
      width: 100%;
    }
    
    .delivery-option:last-child {
      border-bottom: none;
    }
    
    .delivery-option input {
      display: none;
    }
    
    .delivery-option label {
      display: block;
      cursor: pointer;
      width: 100%;
      height: 100%;
      font-size: 0.9rem;
    }
    
    .delivery-option.selected {
      background-color: var(--primary-color);
      color: white;
    }
    
    /* Modal de Adicionais */
    .addons-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.7);
      z-index: 1003;
      overflow-y: auto;
      -webkit-overflow-scrolling: touch;
    }
    
    .addons-content {
      background-color: white;
      margin: 1.5rem auto;
      padding: 1.2rem;
      border-radius: 8px;
      max-width: 95%;
      width: 100%;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      box-sizing: border-box;
    }
    
    .addon-option {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0.8rem 0;
      border-bottom: 1px solid #eee;
    }
    
    .addon-option:last-child {
      border-bottom: none;
    }
    
    .addon-name {
      flex: 1;
    }
    
    .addon-price {
      margin-left: 1rem;
      color: var(--primary-color);
      font-weight: bold;
    }
    
    .addon-checkbox {
      margin-left: 1rem;
      width: 20px;
      height: 20px;
    }
    
    .addons-actions {
      display: flex;
      justify-content: space-between;
      margin-top: 1rem;
      width: 100%;
      gap: 0.5rem;
    }
    
    .addons-actions button {
      flex: 1;
      padding: 0.7rem;
      font-size: 0.9rem;
    }
    
    /* Modal de Prévia do Pedido */
    .preview-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.7);
      z-index: 1004;
      overflow-y: auto;
      -webkit-overflow-scrolling: touch;
    }
    
    .preview-content {
      background-color: white;
      margin: 1.5rem auto;
      padding: 1.2rem;
      border-radius: 8px;
      max-width: 95%;
      width: 100%;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
      box-sizing: border-box;
    }
    
    .preview-item {
      display: flex;
      flex-direction: column;
      padding: 0.5rem 0;
      border-bottom: 1px solid #eee;
      width: 100%;
    }
    
    .preview-item-row {
      display: flex;
      justify-content: space-between;
      width: 100%;
    }
    
    .preview-item-name {
      flex: 2;
      font-size: 0.9rem;
      word-break: break-word;
    }
    
    .preview-item-price {
      flex: 1;
      text-align: right;
      font-size: 0.9rem;
    }
    
    .preview-item-remove {
      color: var(--danger-color);
      margin-left: 0.5rem;
      cursor: pointer;
      background: none;
      border: none;
      font-size: 0.8rem;
    }
    
    .preview-item-quantity {
      display: flex;
      align-items: center;
      margin-top: 0.3rem;
      width: 100%;
      justify-content: flex-start;
    }
    
    .preview-item-notes {
      width: 100%;
      font-size: 0.75rem;
      color: #666;
      margin-top: 0.3rem;
      font-style: italic;
      word-break: break-word;
    }
    
    .preview-actions {
      display: flex;
      justify-content: space-between;
      margin-top: 1rem;
      width: 100%;
      gap: 0.5rem;
    }
    
    .preview-actions button {
      flex: 1;
      padding: 0.7rem;
      font-size: 0.9rem;
    }
    
    /* Seções Salgada e Doce */
    .section-salty {
      background-color: var(--salty-section);
      padding: 0.8rem;
      margin: 0.5rem 0;
      border-radius: 4px;
    }
    
    .section-sweet {
      background-color: var(--sweet-section);
      padding: 0.8rem;
      margin: 0.5rem 0;
      border-radius: 4px;
    }
    
    .section-title {
      font-weight: bold;
      margin-bottom: 0.5rem;
      color: var(--dark-color);
      font-size: 0.9rem;
      text-transform: uppercase;
    }
    
    /* Estilos para o mapa */
    #map-container {
      margin-top: 10px;
      padding: 10px;
      background-color: #f5f5f5;
      border-radius: 4px;
      text-align: center;
      position: relative;
      height: 300px;
      overflow: hidden;
    }
    
    #map {
      width: 100%;
      height: 100%;
      background-color: #e8f4f8;
      position: relative;
    }
    
    .map-marker {
      position: absolute;
      width: 12px;
      height: 12px;
      background-color: red;
      border-radius: 50%;
      transform: translate(-50%, -50%);
      z-index: 10;
    }
    
    .map-marker::after {
      content: '';
      position: absolute;
      width: 20px;
      height: 20px;
      background-color: rgba(255, 0, 0, 0.3);
      border-radius: 50%;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    
    .map-marker.client {
      background-color: blue;
    }
    
    .map-marker.client::after {
      background-color: rgba(0, 0, 255, 0.3);
    }
    
    .map-route {
      position: absolute;
      height: 2px;
      background-color: var(--primary-color);
      transform-origin: 0 0;
      z-index: 5;
    }
    
    .map-labels {
      position: absolute;
      font-size: 10px;
      background-color: white;
      padding: 2px 4px;
      border-radius: 2px;
      z-index: 20;
    }
    
    #map-info {
      margin-top: 10px;
      font-size: 12px;
      text-align: center;
    }
    
    #map-buttons {
      display: flex;
      justify-content: center;
      gap: 10px;
      margin-top: 10px;
    }
    
    #map-buttons button {
      padding: 8px 15px;
      background-color: var(--primary-color);
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 0.9rem;
    }
    
    #map-buttons button:hover {
      background-color: var(--secondary-color);
    }
    
    /* Responsividade para tablets */
    @media (min-width: 600px) {
      .header h1 {
        font-size: 1.8rem;
      }
      
      .header p {
        font-size: 0.9rem;
      }
      
      .tab-button {
        padding: 0.7rem 1rem;
        font-size: 0.8rem;
      }
      
      .container {
        padding: 1rem;
      }
      
      .item {
        flex-direction: row;
      }
      
      .item-image {
        width: 120px;
        height: 120px;
        margin-right: 1rem;
        margin-bottom: 0;
      }
      
      .item-details {
        width: calc(100% - 136px);
      }
      
      .add-to-cart {
        width: auto;
        min-width: 120px;
      }
      
      .modal-content, .notes-content, .item-modal-content, .addons-content, .preview-content {
        max-width: 500px;
        padding: 1.5rem;
      }
      
      .delivery-options {
        flex-direction: row;
      }
      
      .delivery-option {
        border-right: 1px solid #ddd;
        border-bottom: none;
      }
      
      .delivery-option:last-child {
        border-right: none;
      }
      
      .payment-options {
        flex-wrap: nowrap;
      }
      
      /* Ajustes para o carrinho em tablets */
      .cart-section {
        max-height: 50vh;
      }
      
      .cart-items {
        max-height: 200px;
      }
      
      .cart-actions {
        flex-direction: row;
      }
      
      .preview-actions {
        flex-direction: row;
      }
    }
    
    /* Responsividade para desktops */
    @media (min-width: 900px) {
      .container {
        flex-direction: row;
        max-width: 1200px;
        padding-bottom: 0;
      }
      
      .menu-section {
        padding-right: 1rem;
        margin-bottom: 0;
        flex: 1;
      }
      
      .cart-section {
        position: sticky;
        top: 60px;
        height: calc(100vh - 60px);
        bottom: auto;
        max-width: 320px;
        max-height: none;
        transform: none !important;
        overflow-y: auto;
        box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      }
      
      .item-image {
        width: 100px;
        height: 100px;
      }
      
      .item-details {
        width: calc(100% - 116px);
      }
      
      /* Ajuste para o carrinho flutuante acompanhar o scroll */
      .cart-section {
        position: -webkit-sticky;
        position: sticky;
        align-self: flex-start;
        overflow-y: auto;
      }
      
      /* Garante que os botões do carrinho sejam visíveis */
      .cart-actions {
        position: sticky;
        bottom: 0;
        background-color: rgba(255, 255, 255, 0.95);
        padding: 0.8rem 0;
        margin-bottom: -0.8rem;
      }
      
      .preview-content {
        max-width: 600px;
      }
    }
    
    /* Ajustes específicos para mobile */
    @media (max-width: 599px) {
      /* Garante que os botões do carrinho sejam visíveis */
      .cart-section {
        padding-bottom: 120px; /* Espaço extra para os botões */
      }
      
      .cart-actions {
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(255, 255, 255, 0.95);
        padding: 0.8rem;
        box-shadow: 0 -2px 5px rgba(0,0,0,0.1);
        z-index: 91;
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
      }
      
      /* Ajusta a altura do container de itens do carrinho */
      .cart-items {
        max-height: calc(40vh - 150px); /* Altura total menos espaço dos botões e outros elementos */
      }
      
      .preview-actions {
        flex-direction: column;
      }
    }
    
    /* Animations */
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .category {
      animation: fadeIn 0.5s ease-out forwards;
    }
    
    /* Delay animations for each category */
    .category:nth-child(1) { animation-delay: 0.1s; }
    .category:nth-child(2) { animation-delay: 0.2s; }
    .category:nth-child(3) { animation-delay: 0.3s; }
    .category:nth-child(4) { animation-delay: 0.4s; }
    .category:nth-child(5) { animation-delay: 0.5s; }
    .category:nth-child(6) { animation-delay: 0.6s; }
    .category:nth-child(7) { animation-delay: 0.7s; }
  </style>
</head>
<body>
  <div class="header">
    <img src="logotipo1pitiu.png" alt="FoodTruck do Pitiu" class="logo">
    <h1>𝙁𝙊𝙊𝘿𝙏𝙍𝙐𝘾𝙆 𝘿𝙊 𝙋𝙄𝙏𝙄𝙐</h1>
    <p id="status-text" class="status closed">Fechado</p>
    <p>📍 Praça Saiqui, 157 - Vila Valqueire, Rio de Janeiro - RJ, 21330-320</p>
    <p>🛵 Cardápio impresso::Instagram::Whatsapp: é só clicar ⤵️</p>
    <div class="social-links">
      <a href="https://www.canva.com/design/DAFiXrcSAYE/SyFYhg2E6JroZstX3cA_hA/view?website#4" target="_blank" title="Menuimpresso"><i class="fas fa-book-open"></i></a>
      <a href="https://www.instagram.com/foodtruckdopitiu/" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a>
      <a href="https://wa.me/5521992254487" target="_blank" title="WhatsApp"><i class="fab fa-whatsapp"></i></a>
    </div>
  </div>

  <!-- Botão de voltar ao topo -->
  <div id="back-to-top" class="back-to-top">
    <i class="fas fa-arrow-up"></i>
  </div>
  
  <div class="tabs">
    <div class="tab-button active" onclick="scrollToSection('hamburgueres')">Hambúrgueres</div>
    <div class="tab-button" onclick="scrollToSection('pao-queijo')">Pão de Queijo</div>
    <div class="tab-button" onclick="scrollToSection('pastelzinho')">Pastelzinho</div>
    <div class="tab-button" onclick="scrollToSection('petiscos')">Petiscos</div>
    <div class="tab-button" onclick="scrollToSection('bebidas')">Bebidas</div>
    <div class="tab-button" onclick="scrollToSection('smoothie')">Smoothie</div>
    <div class="tab-button" onclick="scrollToSection('cervejas')">Cervejas</div>
  </div>

  <div class="container">
    <div class="menu-section">
      <!-- Hambúrgueres -->
      <div id="hamburgueres" class="category">
        <div class="category-header">Hambúrgueres Artesanais</div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,1" alt="Carne no Prato" class="item-image" onclick="openItemModal('Carne no Prato', 'Blend da casa de 180g, queijo prato e mussarela no pão brioche.', 'https://source.unsplash.com/random/300x300/?burger,1')">
          <div class="item-details">
            <h3 class="item-title">Carne no Prato - R$18</h3>
            <p class="item-description">Blend da casa de 180g, queijo prato e mussarela no pão brioche.</p>
            <div class="item-price">R$ 18,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="openAddonsModal('Carne no Prato', 18, 'https://source.unsplash.com/random/300x300/?burger,1')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Carrinho de Compras -->
    <div class="cart-section">
      <h2 class="cart-title">Seu Pedido</h2>
      <div id="cart-items" class="cart-items">
        <div class="empty-cart">Seu carrinho está vazio</div>
      </div>
      <div id="cart-total" class="cart-total">Total: R$ 0,00</div>
      <div class="cart-actions">
        <button class="cart-button preview-button" onclick="openPreviewModal()">Ver Prévia do Pedido</button>
        <button class="cart-button checkout-button" onclick="openCheckoutModal()">Fechar Pedido</button>
        <button class="cart-button clear-button" onclick="clearCart()">Limpar Carrinho</button>
      </div>
    </div>
  </div>

  <!-- Modal de Checkout -->
  <div id="checkout-modal" class="modal">
    <div class="modal-content">
      <span class="close-modal" onclick="closeModal()">&times;</span>
      <h2>Finalizar Pedido</h2>
      
      <form id="checkout-form">
        <div class="form-group">
          <label for="customer-name">1. Seu nome / Celular:</label>
          <input type="text" id="customer-name" placeholder="Nome completo" required>
          <input type="tel" id="customer-phone" placeholder="Celular (com DDD)" required style="margin-top: 0.5rem;">
        </div>
        
        <div class="form-group">
          <label>2. Pedido completo:</label>
          <div id="order-summary" class="order-summary">
            <!-- Itens do pedido serão inseridos aqui pelo JavaScript -->
          </div>
        </div>
        
        <div class="form-group">
          <label>3. Opção de retirada:</label>
          <div class="delivery-options">
            <div class="delivery-option" onclick="selectDeliveryOption(this, 'retirada')">
              <input type="radio" id="option-retirada" name="delivery-option" value="retirada">
              <label for="option-retirada">Retirada</label>
            </div>
            <div class="delivery-option" onclick="selectDeliveryOption(this, 'local')">
              <input type="radio" id="option-local" name="delivery-option" value="local">
              <label for="option-local">Comer no Local</label>
            </div>
            <div class="delivery-option" onclick="selectDeliveryOption(this, 'entrega')">
              <input type="radio" id="option-entrega" name="delivery-option" value="entrega" checked>
              <label for="option-entrega">Entrega</label>
            </div>
          </div>
        </div>
        
        <div id="address-fields" class="form-group">
          <label for="customer-address">4. Endereço completo:</label>
          <input type="text" id="customer-street" placeholder="Rua" required>
          <input type="text" id="customer-number" placeholder="Número" required style="margin-top: 0.5rem;">
          <input type="text" id="customer-complement" placeholder="Complemento (apto/casa/local)" style="margin-top: 0.5rem;">
          <input type="text" id="customer-neighborhood" placeholder="Bairro" required style="margin-top: 0.5rem;">
          <button type="button" onclick="calculateDeliveryFeeByAddress()" style="margin-top: 0.5rem; padding: 0.7rem; background-color: var(--primary-color); color: white; border: none; border-radius: 4px; cursor: pointer; width: 100%;">
            Calcular Taxa de Entrega
          </button>
        </div>
        
        <div id="delivery-fee" class="delivery-fee">
          Taxa de entrega: R$ 0,00
        </div>
        
        <div id="map-container" style="display: none;">
          <div id="map">
            <!-- Mapa será renderizado aqui -->
          </div>
          <div id="map-info">
            Distância calculada: <span id="distance-display">0</span> km<br>
            Tempo estimado: <span id="time-display">0</span> min
          </div>
          <div id="map-buttons">
            <button type="button" onclick="confirmDeliveryFee()">Confirmar Taxa</button>
            <button type="button" onclick="recalculateDeliveryFee()">Recalcular</button>
          </div>
        </div>
        
        <div class="form-group">
          <label>5. Forma de pagamento:</label>
          <div class="payment-options">
            <div class="payment-option">
              <input type="radio" id="payment-pix" name="payment" value="PIX" checked>
              <label for="payment-pix">PIX</label>
              <div class="payment-dot"></div>
            </div>
            <div class="payment-option">
              <input type="radio" id="payment-cash" name="payment" value="Dinheiro">
              <label for="payment-cash">Dinheiro</label>
              <div class="payment-dot"></div>
            </div>
            <div class="payment-option">
              <input type="radio" id="payment-card" name="payment" value="Cartão Crédito/Débito">
              <label for="payment-card">Cartão Crédito/Débito</label>
              <div class="payment-dot"></div>
            </div>
          </div>
        </div>
        
        <!-- Campo para troco quando pagamento em dinheiro -->
        <div id="change-field" class="form-group" style="display: none;">
          <label for="customer-change">Troco para quanto?</label>
          <input type="text" id="customer-change" placeholder="Valor para troco (opcional)">
        </div>
        
        <div id="order-total" class="order-total">
          Total do Pedido: R$ 0,00
        </div>
        
        <button type="button" class="submit-order" onclick="submitOrder()">Confirmar Pedido</button>
      </form>
    </div>
  </div>

  <!-- Modal de Observação -->
  <div id="notes-modal" class="notes-modal">
    <div class="notes-content">
      <span class="close-modal" onclick="closeNotesModal()">&times;</span>
      <h2 id="notes-item-title">Inserir observação?</h2>
      
      <div class="form-group">
        <label for="item-notes">Observações (opcional):</label>
        <textarea id="item-notes" placeholder="Ex: sem cebola, bem passado, etc."></textarea>
      </div>
      
      <div class="notes-actions">
        <button type="button" class="submit-order" style="background-color: #666;" onclick="closeNotesModal()">Cancelar</button>
        <button type="button" class="submit-order" onclick="addItemWithNotes()">Adicionar</button>
      </div>
    </div>
  </div>

  <!-- Modal de Visualização do Item -->
  <div id="item-modal" class="item-modal">
    <div class="item-modal-content">
      <span class="close-modal" onclick="closeItemModal()">&times;</span>
      <img id="item-modal-image" src="" alt="" class="item-modal-image">
      <h3 id="item-modal-title" class="item-modal-title"></h3>
      <p id="item-modal-description" class="item-modal-description"></p>
    </div>
  </div>

  <!-- Modal de Adicionais -->
  <div id="addons-modal" class="addons-modal">
    <div class="addons-content">
      <span class="close-modal" onclick="closeAddonsModal()">&times;</span>
      <h2 id="addons-item-title">Adicionais</h2>
      
      <div id="addons-list">
        <!-- Adicionais serão inseridos aqui pelo JavaScript -->
      </div>
      
      <div class="form-group">
        <label for="addons-notes">Observações (opcional):</label>
        <textarea id="addons-notes" placeholder="Ex: sem cebola, sem maionese, etc."></textarea>
      </div>
      
      <div class="addons-actions">
        <button type="button" class="submit-order" style="background-color: #666;" onclick="closeAddonsModal()">Cancelar</button>
        <button type="button" class="submit-order" onclick="addItemWithAddons()">Adicionar ao Carrinho</button>
      </div>
    </div>
  </div>

  <!-- Modal de Prévia do Pedido -->
  <div id="preview-modal" class="preview-modal">
    <div class="preview-content">
      <span class="close-modal" onclick="closePreviewModal()">&times;</span>
      <h2>Prévia do Pedido</h2>
      
      <div id="preview-items" class="order-summary">
        <!-- Itens do pedido serão inseridos aqui pelo JavaScript -->
      </div>
      
      <div id="preview-total" class="order-total">
        Total: R$ 0,00
      </div>
      
      <div class="preview-actions">
        <button type="button" class="submit-order" style="background-color: #666;" onclick="closePreviewModal()">Incluir mais itens</button>
        <button type="button" class="submit-order" onclick="openCheckoutModal()">Fechar Pedido</button>
        <button type="button" class="submit-order" style="background-color: var(--danger-color);" onclick="clearCart(); closePreviewModal();">Limpar Carrinho</button>
      </div>
    </div>
  </div>

<script>
    let cart = [];
    let currentItem = null;
    let currentAddons = [];
    let orderNumber = 1000;
    let deliveryFee = 0;
    let clientCoords = null;
    let distance = 0;
    
    // Coordenadas do estabelecimento (Praça Saiqui, 157)
    const ESTABLISHMENT_COORDS = {
        lat: -22.8758,
        lng: -43.3619
    };
    
    // Lista de adicionais para hambúrgueres
    const hamburgerAddons = [
      { name: "Carne", price: 8.00 },
      { name: "Bacon ou Calabresa", price: 4.00 },
      { name: "Cheddar ou Catupiry", price: 5.00 },
      { name: "Queijo Prato ou Mussarela", price: 1.50 },
      { name: "Ovo", price: 1.00 },
      { name: "Cebola Caramelizada", price: 2.00 },
      { name: "Trocar pão tradicional por pão de queijo", price: 4.00 },
      { name: "Não incluir nada", price: 0.00 }
    ];
    
    // Verifica se está no horário de funcionamento
    function checkBusinessHours() {
      const now = new Date();
      const hours = now.getHours();
      const statusElement = document.getElementById('status-text');
      
      // Aberto de domingo a domingo das 19h às 00h
      if (hours >= 7 || hours < 0) {
        statusElement.textContent = 'Aberto';
        statusElement.className = 'status open';
        return true;
      } else {
        statusElement.textContent = 'Fechado';
        statusElement.className = 'status closed';
        return false;
      }
    }
    
    // Atualiza o carrinho no localStorage
    function updateLocalStorage() {
      localStorage.setItem('cart', JSON.stringify(cart));
    }
    
    // Carrega o carrinho do localStorage ao carregar a página
    function loadCart() {
      const savedCart = localStorage.getItem('cart');
      if (savedCart) {
        cart = JSON.parse(savedCart);
        updateCart();
      }
    }
    
    // Adiciona item ao carrinho
    function addItem(name, price, image, addonsList = [], notes = '', event = null) {
      let itemName = name;
      let itemPrice = price;
      let addonsDescription = '';
      
      if (addonsList && addonsList.length > 0) {
        addonsDescription = ' (Adicionais: ';
        addonsList.forEach((addon, index) => {
          itemPrice += addon.price;
          addonsDescription += addon.name;
          if (index < addonsList.length - 1) {
            addonsDescription += ', ';
          }
        });
        addonsDescription += ')';
        itemName += addonsDescription;
      }
      
      const existingItem = cart.find(item => item.name === itemName && item.notes === notes);
      
      if (existingItem) {
        existingItem.quantity += 1;
      } else {
        cart.push({ 
          name: itemName, 
          price: itemPrice, 
          basePrice: price,
          image: image, 
          quantity: 1,
          addons: addonsList,
          notes: notes
        });
      }
      
      updateCart();
      updateLocalStorage();
      
      // Feedback visual
      const button = event ? event.target : null;
      if (button) {
        button.textContent = 'Adicionado!';
        button.style.backgroundColor = '#27ae60';
        setTimeout(() => {
          button.textContent = 'Adicionar';
          button.style.backgroundColor = '';
        }, 1000);
      }
    }
    
    // Remove item do carrinho
    function removeItem(index) {
      cart.splice(index, 1);
      updateCart();
      updateLocalStorage();
    }
    
    // Atualiza a quantidade de um item no carrinho
    function updateQuantity(index, newQuantity) {
      if (newQuantity < 1) {
        removeItem(index);
        return;
      }
      
      cart[index].quantity = newQuantity;
      updateCart();
      updateLocalStorage();
    }
    
    // Atualiza a exibição do carrinho
    function updateCart() {
      const cartItemsElement = document.getElementById('cart-items');
      const cartTotalElement = document.getElementById('cart-total');
      
      if (cart.length === 0) {
        cartItemsElement.innerHTML = '<div class="empty-cart">Seu carrinho está vazio</div>';
        cartTotalElement.textContent = 'Total: R$ 0,00';
        return;
      }
      
      let itemsHTML = '';
      let total = 0;
      
      cart.forEach((item, index) => {
        const itemTotal = item.price * item.quantity;
        total += itemTotal;
        
        itemsHTML += `
          <div class="cart-item">
            <div class="cart-item-row">
              <div class="cart-item-name">
                ${item.name}
                <button class="cart-item-remove" onclick="removeItem(${index})">
                  <i class="fas fa-trash"></i>
                </button>
              </div>
              <div class="cart-item-price">R$ ${itemTotal.toFixed(2)}</div>
            </div>
            <div class="cart-item-quantity">
              <button class="quantity-btn" onclick="updateQuantity(${index}, ${item.quantity - 1})">-</button>
              <span class="quantity-value">${item.quantity}</span>
              <button class="quantity-btn" onclick="updateQuantity(${index}, ${item.quantity + 1})">+</button>
            </div>
            ${item.notes ? `<div class="cart-item-notes">Obs: ${item.notes}</div>` : ''}
          </div>
        `;
      });
      
      cartItemsElement.innerHTML = itemsHTML;
      cartTotalElement.textContent = `Total: R$ ${total.toFixed(2)}`;
    }
    
    // Limpa o carrinho
    function clearCart() {
      cart = [];
      updateCart();
      updateLocalStorage();
    }
    
    // Abre o modal de prévia do pedido
    function openPreviewModal() {
      if (cart.length === 0) {
        alert('Seu carrinho está vazio!');
        return;
      }
      
      const modal = document.getElementById('preview-modal');
      modal.style.display = 'block';
      
      // Atualiza o resumo do pedido no modal
      const previewItems = document.getElementById('preview-items');
      const previewTotal = document.getElementById('preview-total');
      let summaryHTML = '';
      let total = 0;
      
      cart.forEach((item, index) => {
        const itemTotal = item.price * item.quantity;
        total += itemTotal;
        
        summaryHTML += `
          <div class="preview-item">
            <div class="preview-item-row">
              <div class="preview-item-name">
                ${item.quantity}x ${item.name}
                <button class="preview-item-remove" onclick="removeItem(${index}); updatePreviewModal();">
                  <i class="fas fa-trash"></i>
                </button>
              </div>
              <div class="preview-item-price">R$ ${itemTotal.toFixed(2)}</div>
            </div>
            <div class="preview-item-quantity">
              <button class="quantity-btn" onclick="updateQuantity(${index}, ${item.quantity - 1}); updatePreviewModal();">-</button>
              <span class="quantity-value">${item.quantity}</span>
              <button class="quantity-btn" onclick="updateQuantity(${index}, ${item.quantity + 1}); updatePreviewModal();">+</button>
            </div>
            ${item.notes ? `<div class="preview-item-notes">Obs: ${item.notes}</div>` : ''}
          </div>
        `;
      });
      
      summaryHTML += `
        <div class="order-item" style="border-top: 1px solid #ddd; padding-top: 0.5rem;">
          <span><strong>Subtotal</strong></span>
          <span><strong>R$ ${total.toFixed(2)}</strong></span>
        </div>
      `;
      
      previewItems.innerHTML = summaryHTML;
      previewTotal.textContent = `Total: R$ ${total.toFixed(2)}`;
    }
    
    // Atualiza o modal de prévia do pedido
    function updatePreviewModal() {
      if (document.getElementById('preview-modal').style.display === 'block') {
        openPreviewModal();
      }
    }
    
    // Fecha o modal de prévia do pedido
    function closePreviewModal() {
      const modal = document.getElementById('preview-modal');
      modal.style.display = 'none';
    }
    
    // Abre o modal de checkout
    function openCheckoutModal() {
      if (cart.length === 0) {
        alert('Seu carrinho está vazio!');
        return;
      }
      
      // Fecha o modal de prévia se estiver aberto
      closePreviewModal();
      
      // Verifica se está no horário de funcionamento
      if (!checkBusinessHours()) {
        alert('Desculpe, estamos fechados no momento. Nosso horário de funcionamento é de domingo a domingo das 19h às 00h.');
        return;
      }
      
      const modal = document.getElementById('checkout-modal');
      modal.style.display = 'block';
      
      // Atualiza o resumo do pedido no modal
      const orderSummary = document.getElementById('order-summary');
      let summaryHTML = '';
      let subtotal = 0;
      
      cart.forEach(item => {
        const itemTotal = item.price * item.quantity;
        subtotal += itemTotal;
        
        summaryHTML += `
          <div class="order-item">
            <span>${item.quantity}x ${item.name}</span>
            <span>R$ ${itemTotal.toFixed(2)}</span>
          </div>
          ${item.notes ? `<div class="order-item" style="font-size: 0.8rem; color: #666;">- Obs: ${item.notes}</div>` : ''}
        `;
      });
      
      summaryHTML += `
        <div class="order-item" style="border-top: 1px solid #ddd; padding-top: 0.5rem;">
          <span><strong>Subtotal</strong></span>
          <span><strong>R$ ${subtotal.toFixed(2)}</strong></span>
        </div>
      `;
      
      orderSummary.innerHTML = summaryHTML;
      
      // Atualiza o total no modal
      updateOrderTotal();
    }
    
    // Fecha o modal
    function closeModal() {
      const modal = document.getElementById('checkout-modal');
      modal.style.display = 'none';
    }
    
    // Seleciona opção de entrega/retirada
    function selectDeliveryOption(element, option) {
      // Remove a seleção de todos os botões
      document.querySelectorAll('.delivery-option').forEach(btn => {
        btn.classList.remove('selected');
      });
      
      // Adiciona seleção ao botão clicado
      element.classList.add('selected');
      
      // Marca o radio button correspondente
      document.getElementById(`option-${option}`).checked = true;
      
      // Mostra/oculta campos de endereço conforme necessário
      const addressFields = document.getElementById('address-fields');
      const deliveryFeeElement = document.getElementById('delivery-fee');
      const mapContainer = document.getElementById('map-container');
      
      if (option === 'entrega') {
        addressFields.style.display = 'block';
        deliveryFeeElement.style.display = 'block';
        mapContainer.style.display = 'none';
      } else if (option === 'retirada' || option === 'local') {
        addressFields.style.display = 'none';
        deliveryFeeElement.style.display = 'none';
        mapContainer.style.display = 'none';
        deliveryFeeElement.textContent = 'Taxa de entrega: R$ 0,00';
        deliveryFee = 0;
      }
      
      updateOrderTotal();
    }
    
    // Função para calcular a distância entre duas coordenadas (Haversine formula)
    function calculateDistance(lat1, lon1, lat2, lon2) {
        const R = 6371; // Raio da Terra em km
        const dLat = (lat2 - lat1) * Math.PI / 180;
        const dLon = (lon2 - lon1) * Math.PI / 180;
        const a = 
            Math.sin(dLat/2) * Math.sin(dLat/2) +
            Math.cos(lat1 * Math.PI / 180) * Math.cos(lat2 * Math.PI / 180) * 
            Math.sin(dLon/2) * Math.sin(dLon/2);
        const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));
        return R * c; // Distância em km
    }

    // Função para obter coordenadas do endereço (simulação)
    function getCoordinatesFromAddress(street, neighborhood) {
        // Esta é uma simulação - em uma aplicação real você precisaria de uma API de geocoding
        // Aqui estou retornando coordenadas aleatórias dentro de um raio de 20km do estabelecimento
        // para fins de demonstração
        
        // Usa o nome da rua e bairro como seed para gerar coordenadas consistentes
        const seed = (street + neighborhood).split('').reduce((acc, char) => acc + char.charCodeAt(0), 0);
        const randomFactor = (seed % 1000) / 1000; // Fator baseado no endereço
        
        // Gera um ângulo aleatório baseado no endereço
        const angle = randomFactor * 2 * Math.PI;
        
        // Gera uma distância aleatória baseada no endereço (entre 1km e 20km)
        const distance = 1 + (randomFactor * 19);
        
        // Calcula novas coordenadas baseadas na distância e ângulo
        const earthRadius = 6371; // km
        const lat1 = ESTABLISHMENT_COORDS.lat * Math.PI / 180;
        const lon1 = ESTABLISHMENT_COORDS.lng * Math.PI / 180;
        
        const lat2 = Math.asin(Math.sin(lat1) * Math.cos(distance/earthRadius) + 
                     Math.cos(lat1) * Math.sin(distance/earthRadius) * Math.cos(angle));
        const lon2 = lon1 + Math.atan2(Math.sin(angle) * Math.sin(distance/earthRadius) * Math.cos(lat1), 
                     Math.cos(distance/earthRadius) - Math.sin(lat1) * Math.sin(lat2));
        
        return {
            lat: lat2 * 180 / Math.PI,
            lng: lon2 * 180 / Math.PI
        };
    }

    // Função para calcular a taxa de entrega baseada na distância
    function calculateFeeByDistance(distance) {
        if (distance <= 2) return 5;
        if (distance <= 5) return 8;
        if (distance <= 10) return 12;
        if (distance <= 15) return 15;
        if (distance <= 20) return 18;
        return 25; // Para distâncias maiores que 20km
    }

    // Função para renderizar o mapa com a rota
    function renderMap(establishmentCoords, clientCoords, distance) {
        const mapContainer = document.getElementById('map-container');
        const mapElement = document.getElementById('map');
        
        // Limpa o mapa anterior
        mapElement.innerHTML = '';
        
        // Cria elementos do mapa
        const establishmentMarker = document.createElement('div');
        establishmentMarker.className = 'map-marker';
        establishmentMarker.style.left = '20%';
        establishmentMarker.style.top = '20%';
        
        const clientMarker = document.createElement('div');
        clientMarker.className = 'map-marker client';
        clientMarker.style.left = '80%';
        clientMarker.style.top = '80%';
        
        // Calcula ângulo para a linha de rota
        const angle = Math.atan2(80 - 20, 80 - 20) * 180 / Math.PI;
        const length = Math.sqrt(Math.pow(80 - 20, 2) + Math.pow(80 - 20, 2));
        
        const routeLine = document.createElement('div');
        routeLine.className = 'map-route';
        routeLine.style.width = `${length}%`;
        routeLine.style.left = '20%';
        routeLine.style.top = '20%';
        routeLine.style.transform = `rotate(${angle}deg)`;
        
        // Adiciona rótulos
        const establishmentLabel = document.createElement('div');
        establishmentLabel.className = 'map-labels';
        establishmentLabel.textContent = 'FoodTruck';
        establishmentLabel.style.left = '25%';
        establishmentLabel.style.top = '25%';
        
        const clientLabel = document.createElement('div');
        clientLabel.className = 'map-labels';
        clientLabel.textContent = 'Seu endereço';
        clientLabel.style.left = '85%';
        clientLabel.style.top = '85%';
        
        // Adiciona elementos ao mapa
        mapElement.appendChild(establishmentMarker);
        mapElement.appendChild(clientMarker);
        mapElement.appendChild(routeLine);
        mapElement.appendChild(establishmentLabel);
        mapElement.appendChild(clientLabel);
        
        // Atualiza informações de distância e tempo
        document.getElementById('distance-display').textContent = distance.toFixed(1);
        document.getElementById('time-display').textContent = Math.round(distance * 3); // Estimativa de 3 min/km
        
        // Mostra o container do mapa
        mapContainer.style.display = 'block';
    }

    // Função para calcular a taxa de entrega baseada no endereço
    function calculateDeliveryFeeByAddress() {
        const street = document.getElementById('customer-street').value;
        const neighborhood = document.getElementById('customer-neighborhood').value;
        const deliveryFeeElement = document.getElementById('delivery-fee');
        
        if (!street || !neighborhood) {
            alert('Por favor, preencha pelo menos a rua e o bairro');
            return;
        }
        
        try {
            // Simula a obtenção de coordenadas do endereço do cliente
            clientCoords = getCoordinatesFromAddress(street, neighborhood);
            
            // Calcula a distância
            distance = calculateDistance(
                ESTABLISHMENT_COORDS.lat, ESTABLISHMENT_COORDS.lng,
                clientCoords.lat, clientCoords.lng
            );
            
            // Arredonda para 1 casa decimal
            distance = Math.round(distance * 10) / 10;
            
            // Calcula a taxa de entrega
            deliveryFee = calculateFeeByDistance(distance);
            
            // Atualiza a exibição
            deliveryFeeElement.innerHTML = `
                Distância estimada: ${distance.toFixed(1)} km<br>
                Taxa de entrega calculada: R$ ${deliveryFee.toFixed(2)}
            `;
            
            // Renderiza o mapa com a rota
            renderMap(ESTABLISHMENT_COORDS, clientCoords, distance);
        } catch (e) {
            console.error('Erro ao calcular distância:', e);
            alert('Não foi possível calcular a distância. Por favor, verifique o endereço e tente novamente.');
        }
        
        // Atualiza o total do pedido
        updateOrderTotal();
    }

    // Função para confirmar a taxa de entrega
    function confirmDeliveryFee() {
        const deliveryFeeElement = document.getElementById('delivery-fee');
        deliveryFeeElement.innerHTML = `Taxa de entrega confirmada: R$ ${deliveryFee.toFixed(2)}`;
        
        // Atualiza o total do pedido
        updateOrderTotal();
    }
    
    // Função para recalculcar a taxa de entrega
    function recalculateDeliveryFee() {
        document.getElementById('map-container').style.display = 'none';
        calculateDeliveryFeeByAddress();
    }
    
    // Atualiza o total do pedido (subtotal + taxa)
    function updateOrderTotal() {
      const deliveryOption = document.querySelector('input[name="delivery-option"]:checked').value;
      const paymentMethod = document.querySelector('input[name="payment"]:checked').value;
      const orderTotalElement = document.getElementById('order-total');
      
      let subtotal = 0;
      cart.forEach(item => {
        subtotal += item.price * item.quantity;
      });
      
      let fee = 0;
      if (deliveryOption === 'entrega') {
        fee = deliveryFee;
      }
      
      const total = subtotal + fee;
      
      orderTotalElement.textContent = `Total do Pedido: R$ ${total.toFixed(2)}`;
      
      // Mostra/oculta campo de troco conforme método de pagamento
      const changeField = document.getElementById('change-field');
      if (paymentMethod === 'Dinheiro') {
        changeField.style.display = 'block';
      } else {
        changeField.style.display = 'none';
      }
    }
    
    // Abre o modal de observação
    function openNotesModal(name, price, image) {
      currentItem = { name, price, image };
      
      const modal = document.getElementById('notes-modal');
      const titleElement = document.getElementById('notes-item-title');
      
      titleElement.textContent = `Inserir observação para ${name}?`;
      document.getElementById('item-notes').value = '';
      
      modal.style.display = 'block';
    }
    
    // Fecha o modal de observação
    function closeNotesModal() {
      const modal = document.getElementById('notes-modal');
      modal.style.display = 'none';
    }
    
    // Adiciona item com observação ao carrinho
    function addItemWithNotes() {
      if (currentItem) {
        const notes = document.getElementById('item-notes').value;
        addItem(currentItem.name, currentItem.price, currentItem.image, [], notes);
        closeNotesModal();
      }
    }
    
    // Abre o modal de adicionais para hambúrgueres
    function openAddonsModal(name, price, image) {
      currentItem = { name, price, image };
      currentAddons = [];
      
      const modal = document.getElementById('addons-modal');
      const titleElement = document.getElementById('addons-item-title');
      const addonsListElement = document.getElementById('addons-list');
      
      titleElement.textContent = `Adicionais para ${name}`;
      document.getElementById('addons-notes').value = '';
      
      // Limpa a lista de adicionais
      addonsListElement.innerHTML = '';
      
      // Adiciona cada opção de adicional
      hamburgerAddons.forEach((addon, index) => {
        const addonElement = document.createElement('div');
        addonElement.className = 'addon-option';
        addonElement.innerHTML = `
          <div class="addon-name">${addon.name}</div>
          <div class="addon-price">R$ ${addon.price.toFixed(2)}</div>
          <input type="checkbox" id="addon-${index}" class="addon-checkbox" 
                 data-name="${addon.name}" data-price="${addon.price}" 
                 onchange="toggleAddon(this, ${index})">
        `;
        addonsListElement.appendChild(addonElement);
      });
      
      modal.style.display = 'block';
    }
    
    // Fecha o modal de adicionais
    function closeAddonsModal() {
      const modal = document.getElementById('addons-modal');
      modal.style.display = 'none';
    }
    
    // Alterna um adicional selecionado
    function toggleAddon(checkbox, index) {
      const addon = hamburgerAddons[index];
      
      if (checkbox.checked) {
        // Se for "Não incluir nada", desmarca todos os outros
        if (addon.name === "Não incluir nada") {
          document.querySelectorAll('.addon-checkbox').forEach(cb => {
            if (cb !== checkbox) cb.checked = false;
          });
          currentAddons = [addon];
        } else {
          // Remove "Não incluir nada" se estiver selecionado
          currentAddons = currentAddons.filter(a => a.name !== "Não incluir nada");
          currentAddons.push(addon);
        }
      } else {
        // Remove o adicional da lista
        currentAddons = currentAddons.filter(a => a.name !== addon.name);
      }
    }
    
    // Adiciona item com adicionais ao carrinho
    function addItemWithAddons() {
      if (currentItem) {
        const notes = document.getElementById('addons-notes').value;
        addItem(currentItem.name, currentItem.price, currentItem.image, currentAddons, notes);
        closeAddonsModal();
      }
    }
    
    // Abre o modal de visualização do item
    function openItemModal(name, description, image) {
      const modal = document.getElementById('item-modal');
      const titleElement = document.getElementById('item-modal-title');
      const descElement = document.getElementById('item-modal-description');
      const imgElement = document.getElementById('item-modal-image');
      
      titleElement.textContent = name;
      descElement.textContent = description;
      imgElement.src = image;
      imgElement.alt = name;
      
      modal.style.display = 'block';
    }
    
    // Fecha o modal de visualização do item
    function closeItemModal() {
      const modal = document.getElementById('item-modal');
      modal.style.display = 'none';
    }
    
    // Gera um código de pedido único
    function generateOrderCode(name, phone, street, number) {
      // Pega as primeiras letras do nome (máximo 2)
      const namePart = name.slice(0, 2).toUpperCase();
      
      // Pega os últimos 2 dígitos do telefone
      const phonePart = phone.slice(-2);
      
      // Pega a primeira letra da rua
      const streetPart = street ? street.charAt(0).toUpperCase() : 'X';
      
      // Pega o último dígito do número
      const numberPart = number ? number.slice(-1) : '0';
      
      // Combina tudo para formar um código de 4 caracteres
      return `${namePart}${phonePart}${streetPart}${numberPart}`;
    }
    
    // Envia o pedido
    function submitOrder() {
      const name = document.getElementById('customer-name').value;
      const phone = document.getElementById('customer-phone').value;
      const deliveryOption = document.querySelector('input[name="delivery-option"]:checked').value;
      const street = document.getElementById('customer-street').value;
      const number = document.getElementById('customer-number').value;
      const complement = document.getElementById('customer-complement').value;
      const zipcode = document.getElementById('customer-zipcode').value;
      const neighborhood = document.getElementById('customer-neighborhood').value;
      const payment = document.querySelector('input[name="payment"]:checked').value;
      const changeFor = payment === 'Dinheiro' ? document.getElementById('customer-change').value : '';
      
      // Validação básica
      if (!name || !phone) {
        alert('Por favor, preencha seu nome e telefone.');
        return;
      }
      
      if (deliveryOption === 'entrega' && (!street || !number || !neighborhood)) {
        alert('Por favor, preencha todos os campos obrigatórios do endereço para entrega.');
        return;
      }
      
      // Incrementa número do pedido
      orderNumber++;
      
      // Gera código do pedido
      const orderCode = generateOrderCode(name, phone, street, number);
      
      // Obtém data e hora atual
      const now = new Date();
      const hours = now.getHours().toString().padStart(2, '0');
      const minutes = now.getMinutes().toString().padStart(2, '0');
      const day = now.getDate().toString().padStart(2, '0');
      const month = (now.getMonth() + 1).toString().padStart(2, '0');
      const year = now.getFullYear();
      
      // Calcula totais
      let subtotal = 0;
      let orderItems = '';
      
      cart.forEach((item, index) => {
        const itemTotal = item.price * item.quantity;
        subtotal += itemTotal;
        orderItems += `${item.quantity}x ${item.name} - R$ ${itemTotal.toFixed(2)}\n`;
        if (item.notes) {
          orderItems += `   Obs: ${item.notes}\n`;
        }
      });
      
      const total = subtotal + (deliveryOption === 'entrega' ? deliveryFee : 0);
      
      // Monta mensagem para WhatsApp
      let message = `*NOVO PEDIDO - FOODTRUCK DO PITIU*\n\n`;
      message += `*Pedido Nº:* ${orderCode}\n`;
      message += `*Data/Hora:* ${hours}:${minutes} em ${day}/${month}/${year}\n\n`;
      message += `*Cliente:* ${name}\n`;
      message += `*Telefone:* ${phone}\n\n`;
      
      if (deliveryOption === 'entrega') {
        message += `*Tipo:* Entrega\n`;
        message += `*Endereço:*\n`;
        message += `${street}, ${number}`;
        if (complement) message += ` - ${complement}`;
        message += `\n${neighborhood}\n`;
        if (zipcode) message += `CEP: ${zipcode}\n`;
        message += `\n*Distância:* ${distance.toFixed(1)} km\n`;
        message += `*Taxa de entrega:* R$ ${deliveryFee.toFixed(2)}\n\n`;
      } else if (deliveryOption === 'retirada') {
        message += `*Tipo:* Retirada\n\n`;
      } else if (deliveryOption === 'local') {
        message += `*Tipo:* Comer no Local\n\n`;
      }
      
      message += `*Pedido:*\n${orderItems}\n`;
      message += `*Subtotal:* R$ ${subtotal.toFixed(2)}\n`;
      message += `*Total:* R$ ${total.toFixed(2)}\n\n`;
      message += `*Forma de pagamento:* ${payment}`;
      
      // Adiciona informação de troco se for pagamento em dinheiro
      if (payment === 'Dinheiro' && changeFor) {
        message += `\n*Troco para:* R$ ${changeFor}`;
      }
      
      // Codifica a mensagem para URL
      const encodedMessage = encodeURIComponent(message);
      
      // Abre o WhatsApp
      window.open(`https://wa.me/5521992254487?text=${encodedMessage}`, '_blank');
      
      // Fecha o modal e limpa o carrinho
      closeModal();
      clearCart();
    }
    
    // Rolagem suave para as seções
    function scrollToSection(sectionId, event) {
      const section = document.getElementById(sectionId);
      if (section) {
        // Atualiza a aba ativa
        if (event && event.target) {
          document.querySelectorAll('.tab-button').forEach(button => {
            button.classList.remove('active');
          });
          event.target.classList.add('active');
        }
        
        // Rolagem suave
        window.scrollTo({
          top: section.offsetTop - 60,
          behavior: 'smooth'
        });
      }
    }
    
    // Observador de interseção para atualizar a aba ativa
    function setupIntersectionObserver() {
      const sections = document.querySelectorAll('.category');
      const navLinks = document.querySelectorAll('.tab-button');
      
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const id = entry.target.id;
            navLinks.forEach(link => {
              link.classList.remove('active');
              if (link.textContent.toLowerCase().includes(id)) {
                link.classList.add('active');
              }
            });
          }
        });
      }, { threshold: 0.5, rootMargin: '-60px 0px -50% 0px' });
      
      sections.forEach(section => {
        observer.observe(section);
      });
    }
    
    // Fecha o modal ao clicar fora dele
    window.onclick = function(event) {
      const checkoutModal = document.getElementById('checkout-modal');
      const notesModal = document.getElementById('notes-modal');
      const itemModal = document.getElementById('item-modal');
      const addonsModal = document.getElementById('addons-modal');
      const previewModal = document.getElementById('preview-modal');
      
      if (event.target === checkoutModal) {
        closeModal();
      }
      
      if (event.target === notesModal) {
        closeNotesModal();
      }
      
      if (event.target === itemModal) {
        closeItemModal();
      }
      
      if (event.target === addonsModal) {
        closeAddonsModal();
      }
      
      if (event.target === previewModal) {
        closePreviewModal();
      }
    }
    
    // Carrega o carrinho e configura o observador quando a página carrega
    window.addEventListener('DOMContentLoaded', () => {
      loadCart();
      setupIntersectionObserver();
      checkBusinessHours();
      
      // Configura opção de entrega como padrão
      selectDeliveryOption(document.querySelector('.delivery-option:nth-child(3)'), 'entrega');
      
      // Configura o carrinho flutuante
      const cartSection = document.querySelector('.cart-section');
      let lastScrollPosition = window.scrollY;
      
      window.addEventListener('scroll', () => {
        const currentScrollPosition = window.scrollY;
        
        // Esconde o carrinho quando o usuário rola para baixo
        if (currentScrollPosition > lastScrollPosition) {
          cartSection.classList.add('hidden');
        } 
        // Mostra o carrinho quando o usuário rola para cima
        else if (currentScrollPosition < lastScrollPosition) {
          cartSection.classList.remove('hidden');
        }
        
        lastScrollPosition = currentScrollPosition;
      });
      
      // Garante que a aba Hambúrguer esteja visível
      const tabsContainer = document.querySelector('.tabs');
      const hamburgerTab = document.querySelector('.tab-button:first-child');
      if (hamburgerTab) {
        tabsContainer.scrollLeft = 0;
      }
      
      // Atualiza o campo de troco conforme método de pagamento
      document.querySelectorAll('input[name="payment"]').forEach(radio => {
        radio.addEventListener('change', function() {
          updateOrderTotal();
        });
      });

      // Botão de voltar ao topo
      const backToTopButton = document.getElementById('back-to-top');

      window.addEventListener('scroll', () => {
        if (window.pageYOffset > 300) {
          backToTopButton.classList.add('show');
        } else {
          backToTopButton.classList.remove('show');
        }
      });

      backToTopButton.addEventListener('click', () => {
        window.scrollTo({
          top: 0,
          behavior: 'smooth'
        });
      });
    });
</script>
</body>
</html>
