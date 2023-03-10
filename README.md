# wefit

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.



import 'package:flutter/material.dart';

import 'data_converter.dart';

class OrderableList {
  List<OrderableData>? data;
  int? totalRecords = null;

  OrderableList(this.data, this.totalRecords);

  static OrderableList fromMap(Map<String, dynamic> resp2) {
    List? resp = dconvertFull(resp2);
    List<OrderableData>? data = null;
    if (resp != null) {
      data = List<OrderableData>.from(
          resp.map((item) => OrderableData.fromMap(item)));
    }

    int? numRecords = (data == null) ? null : data.length;
    OrderableList oList = OrderableList(data, numRecords);
    return oList;
  }

  @override
  String toString() {
    String st = '';
    st += '==== OrderableList ====\n';
    st += ' TotalRecords: $totalRecords \n';
    st += ' Data: $data \n';
    return st;
  }
}

class OrderableData {
  final int? time;
  final List<ResultableData>? values;

  OrderableData(this.time, this.values);

  static OrderableData fromMap(Map<String, dynamic> resp) {
    List<ResultableData>? vals;
    if (resp['values'] != null) {
      vals = List<ResultableData>.from(
          resp['values'].map((item) => ResultableData.fromMap(item)));
    }
    return OrderableData(
        resp['date_time'] as int?, resp['values'] == null ? null : vals);
  }

  // @override
  // String toString() {
  //   String st = "";
  //   st += "==== OrderableData ====\n";
  //   st += " time: $time \n";
  //   st += " Data: $values \n";
  //   return st;
  // }
}

class ResultableData {
  final String? name;
  final num? value;
  final num? value2;
  final String? unit;
  final String? status;
  final String? statusToDisplay;
  final String? status2;

  ResultableData(
      this.name, this.value, this.unit, this.status, this.value2, this.status2, this.statusToDisplay);

  static ResultableData fromMap(Map<String, dynamic> resp) {
    debugPrint('$resp');
    return ResultableData(
      resp['name'] as String?,
      resp['value'] as num?,
      resp['unit'] as String?,
      resp['status'] as String?,
      resp['value2'] as num?,
      resp['status2'] as String?,
      resp['status_to_display'] as String?,
    );
  }

  @override
  String toString() {
    String st = '';
    st += '\nDate :: ';
    st += ' Name: $name -> ';
    st += ' Value: $value -> ';
    if (value2 != null)
      { st += ' Value2: $value2 -> '; }
    st += ' Unit: $unit -> ';
    st += ' Status: $status ';
    if (status2 != null)
      { st += ' Status: $status2 '; }
    return st;
  }
}#   W e F i t  
 #   W e F i t  
 #   W e F i t  
 