# Orders API Documentation

This document provides comprehensive API documentation for the Orders endpoints in the Scalev API.

## Table of Contents

- [Authentication & Authorization](#authentication--authorization)
- [Core Order Operations](#core-order-operations)
- [Order Status Management](#order-status-management)
- [File Upload Operations](#file-upload-operations)
- [Payment & Settlement](#payment--settlement)
- [Shipping & AWB Operations](#shipping--awb-operations)
- [Chat & Messaging](#chat--messaging)
- [Public Order Operations](#public-order-operations)
- [Utility Operations](#utility-operations)

## Authentication & Authorization

All endpoints require appropriate permissions as defined by the authorization plugs:

- **view_order**: Required for viewing order data, including lists and details
- **edit_order**: Required for modifying orders
- **add_order**: Required for creating new orders
- **delete_order**: Required for deleting orders
- **change_status_order**: Required for changing order statuses
- **create_awb**: Required for requesting pick ups and generating tracking numbers

## Core Order Operations

### List Orders

### Get Order Statistics

### Show Order

### Create Order

### Update Order

### Delete Order

## Order Status Management

### Change Order Status

### Upload Status Changes

### Mark Orders as Not Spam

## File Upload Operations

### Upload Orders

### Upload Receipt

### Update Receipt

## Payment & Settlement

### Create Payment

### Check Order Payment

### Check Order Settlement

## Shipping & AWB Operations

### Generate AWB

### Cancel AWB

### Update Shipment Raw

## Chat & Messaging

### Get Chat Text

### Get Single Chat Text

### Show Message History

### Add Message History

## Public Order Operations

### Show Public Order

### Create Public Order

### Update Public Order

## Utility Operations

### Get Available Actions

### Show by Payment Gateway Reference

### Show by Payment Gateway References

### Update Customer

### Duplicate and Cancel

### Send Digital Product

### Send LMS Access

### Trigger Purchase Event

### Get Order Emails
