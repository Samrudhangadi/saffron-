# saffimport React, { useState, useEffect } from 'react';
import { View, Text, Button, FlatList, StyleSheet } from 'react-native';

// Sample menu for Saffron
const menuItems = [
  { id: '1', name: 'Cappuccino', price: 3.5 },
  { id: '2', name: 'Espresso', price: 2.5 },
  { id: '3', name: 'Cheese Sandwich', price: 5.0 },
  { id: '4', name: 'Pasta Alfredo', price: 8.5 }
];

// Sample special offer
const specialOffer = 'Diwali Sale: Get 20% off on all beverages!';

// Opening and closing hours
const openingHours = '9:30 AM';
const closingHours = '10:15 PM';

const App = () => {
  const [isOpen, setIsOpen] = useState(false);

  useEffect(() => {
    const currentTime = new Date();
    const openingTime = new Date();
    const closingTime = new Date();

    // Set opening time
    const [openingHour, openingMin] = openingHours.split(':');
    openingTime.setHours(openingHour);
    openingTime.setMinutes(openingMin);

    // Set closing time
    const [closingHour, closingMin] = closingHours.split(':');
    closingTime.setHours(closingHour);
    closingTime.setMinutes(closingMin);

    // Check if the restaurant is open
    if (currentTime >= openingTime && currentTime <= closingTime) {
      setIsOpen(true);
    }
  }, []);

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Welcome to Saffron</Text>
      <Text>Status: {isOpen ? 'Open' : 'Closed'}</Text>
      <Text>Hours: {openingHours} - {closingHours}</Text>
      <Text style={styles.offer}>{specialOffer}</Text>

      <Text style={styles.menuTitle}>Menu</Text>
      <FlatList
        data={menuItems}
        keyExtractor={(item) => item.id}
        renderItem={({ item }) => (
          <Text style={styles.menuItem}>
            {item.name} - ${item.price.toFixed(2)}
          </Text>
        )}
      />

      <Button title="Order Now" onPress={() => alert('Order functionality coming soon!')} />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    padding: 20,
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 10,
  },
  offer: {
    color: 'green',
    fontSize: 18,
    marginVertical: 10,
  },
  menuTitle: {
    fontSize: 20,
    fontWeight: 'bold',
    marginVertical: 10,
  },
  menuItem: {
    fontSize: 16,
    marginVertical: 5,
  },
});

export default App;
ron-
