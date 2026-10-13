import React from 'react';
import { View, Text, ScrollView, TouchableOpacity, SafeAreaView, FlatList, Image, Platform } from 'react-native';

const CATEGORIES = ['Áo thun', 'Quần Jean', 'Sơ mi', 'Quần tây', 'Giày lười'];

const PRODUCTS = [
  { id: '1', name: 'Áo thun nam Basic', price: '199.000 đ', oldPrice: '250.000 đ', img: 'https://images.unsplash.com/photo-1506146332389-18140dc7b2fb?w=500' },
  { id: '2', name: 'Áo thun nữ Cotton', price: '229.000 đ', oldPrice: '280.000 đ', img: 'https://images.unsplash.com/photo-1534430480872-3498386e7856?w=500' },
  { id: '3', name: 'Áo sơ mi nam', price: '389.000 đ', oldPrice: '450.000 đ', img: 'https://images.unsplash.com/photo-1517411032315-54ef2cb783bb?w=500' },
  { id: '4', name: 'Áo sơ mi nữ', price: '359.000 đ', oldPrice: '420.000 đ', img: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?w=500' },
  { id: '5', name: 'Quần jean nam', price: '469.000 đ', oldPrice: '550.000 đ', img: 'https://images.unsplash.com/photo-1514432324607-a09d9b4aefdd?w=500' },
  { id: '6', name: 'Quần jean nữ', price: '449.000 đ', oldPrice: '520.000 đ', img: 'https://images.unsplash.com/photo-1509316975850-ff9c5deb0cd9?w=500' },
];

export default function ProductScreen() {
  const renderItem = ({ item }) => (
    <View style={{ flex: 1, margin: 5, backgroundColor: '#fff', borderRadius: 8, overflow: 'hidden' }}>
      <Image source={{ uri: item.img }} style={{ width: '100%', height: 110 }} resizeMode="cover" />
      <View style={{ padding: 8 }}>
        <Text numberOfLines={1} style={{ fontSize: 13, color: '#222', marginBottom: 4 }}>{item.name}</Text>
        <View style={{ flexDirection: 'row', justifyContent: 'space-between' }}>
          <Text style={{ fontSize: 13, color: '#047857', fontWeight: 'bold' }}>{item.price}</Text>
          <Text style={{ fontSize: 11, color: '#aaa', textDecorationLine: 'line-through' }}>{item.oldPrice}</Text>
        </View>
      </View>
    </View>
  );

  return (
    <SafeAreaView style={{ flex: 1, ...(Platform.OS === 'web' ? { backgroundImage: 'linear-gradient(180deg, #ffeef4 0%, #fff 40%, #e0f4ff 100%)' } : { backgroundColor: '#ffeef4' }) }}>
      {/* Header */}
      <View style={{ flexDirection: 'row', justifyContent: 'space-between', padding: 14, alignItems: 'center' }}>
        <Text style={{ fontSize: 24, fontWeight: 'bold' }}>☰</Text>
        <Text style={{ fontSize: 16, fontWeight: '600' }}>👤 Nguyễn Quốc Vương</Text>
      </View>

      {/* Danh mục */}
      <View style={{ paddingHorizontal: 12 }}>
        <Text style={{ fontSize: 16, fontWeight: 'bold', color: '#047857', marginBottom: 10 }}>DANH MỤC SẢN PHẨM</Text>
        <ScrollView horizontal showsHorizontalScrollIndicator={false} style={{ marginBottom: 10 }}>
          {CATEGORIES.map((cat, i) => (
            <View key={i} style={{ backgroundColor: '#fff', paddingVertical: 6, paddingHorizontal: 12, borderRadius: 6, marginRight: 8 }}>
                <Text style={{ fontSize: 13 }}>{cat}</Text>
            </View>
          ))}
        </ScrollView>
      </View>

      {/* Danh sách */}
      <FlatList 
        data={PRODUCTS} 
        renderItem={renderItem} 
        keyExtractor={item => item.id} 
        numColumns={2} 
        contentContainerStyle={{ paddingHorizontal: 8, paddingBottom: 16 }} 
      />
    </SafeAreaView>
  );
}
