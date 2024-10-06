# CC4CaseStudyBasicContactListApplication
	import java.util.Arrays;
	import java.util.Scanner;
	
	public class CaseStudyContactList {
	    public static void main(String[] args) {
			// Create a Scanner object for user input
	        Scanner us_input = new Scanner(System.in);
	
			// Variables for storing user input and managing actions
	        String choice, name_update, em_address_update, contact_num_update;;
			
	        int updating_array_value, access, update, delete, update_choice;
				updating_array_value = 0; // Tracks number of contacts
				access = 0; // Tracks access to specific contacts
				update = 0; // Tracks update operations
				delete = 0; // Tracks delete operations
				
	        boolean valid_choice, valid_action, check;
				valid_choice = false; // Validates user choices
			
			// Arrays to store contact details (name, number, email)
	        String[] name = new String[2];
	        String[] contact_num = new String[2];
	        String[] em_address = new String[2];
			
			// Main program loop for entering the contact list or exiting
	        do {
	            System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
	            System.out.println(String.format("%28s", "===Enter Contact List?==="));
	            System.out.println(String.format("%25s", "|    [Yes] [No]    |"));
				
				// Prompt user to enter "yes" or "no"
	            System.out.print(String.format("%9s", "Choice: "));
	            choice = us_input.next().toLowerCase();
				
				// Handle user choice of yes or no
	            switch (choice) {
	                case "yes":
	                    valid_action = false;
						// Contact list menu loop
	                    do {
							System.out.println(String.format("%30s", "--------------------------------"));
	                        System.out.println(String.format("%30s", "========Contact List========"));
	                        System.out.println(String.format("%5s %s", "[1]", "Display All Contacts"));
	                        System.out.println(String.format("%5s %s", "[2]", "Access Specific Contact"));
	                        System.out.println(String.format("%5s %s", "[3]", "Update Specific Contact"));
	                        System.out.println(String.format("%5s %s", "[4]", "Delete Specific Contact"));
	                        System.out.println(String.format("%5s %s", "[5]", "Input New Contact"));
	                        System.out.println(String.format("%5s %s", "[6]", "Exit Program"));
							
							// Prompt user to choose an action
	                        System.out.print(String.format("%9s", "Action: "));
	                        String action = us_input.next();
							System.out.println(String.format("%30s", "--------------------------------"));
							
							// Execute chosen action
	                        switch (action) {
	                            case "1":	// Display all contacts
	                                valid_action = false;
	                                System.out.println(String.format("%27s", "==Displaying Contacts=="));
									
									// If no contacts, display message
	                                if (updating_array_value == 0) {
	                                    System.out.println("=There are no current contacts!=");
										break;
	                                } else {	// Display stored contacts
	                                    for (int i = 0; i < updating_array_value; i++) {
											System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
	                                        System.out.println(String.format("%20s", "|Contact [" + (i + 1) + "]|"));
	                                        System.out.println(String.format("%7s", "Name: " + name[i]));
	                                        System.out.println(String.format("%17s", "Contact Number: " + contact_num[i]));
	                                        System.out.println(String.format("%16s", "Email Address: " + em_address[i]));
											System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
	                                    }
	                                }
	                                break;
	                            case "2":	// Access a specific contact
	                                valid_action = false;
									do {
										System.out.println(String.format("%28s", "==Accessing Contacts=="));
										
										if (updating_array_value == 0) {
											System.out.println("=There are no current contacts!=");
											break;
										} else {
											for (int i = 0; i < updating_array_value; i++){
												System.out.println(String.format("%16s", "["+ (i + 1) + "] Contact: " + name[i]));
											}
											// Prompt user to access a specific contact
											System.out.println(String.format("%23s", "<- [" + (updating_array_value + 1) + "] Return"));
											System.out.print("which contact do you wish to access?: ");
											access = us_input.nextInt();
											
											// Display chosen contact
											if (access < (updating_array_value + 1) && access != 0){
												System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
												System.out.println(String.format("%27s", "=Displaying Contact [" + access + "]="));
												System.out.println(String.format("%7s", "Name: " + name[access - 1]));
												System.out.println(String.format("%17s", "Contact Number: " + contact_num[access - 1]));
												System.out.println(String.format("%16s", "Email Address: " + em_address[access - 1]));
												System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
											} else if (access == (updating_array_value + 1)){
												System.out.println(String.format("%28s", "=Returning to Contacts="));
												break;
												} else {	
													System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
													System.out.println("The contact of your choice is unknown, please choose what is provided.");
													System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
													valid_action = false;
												}
											}
										} while (!valid_action);
	                                break;
	                            case "3":	// Update a specific contact
	                                valid_action = false;
									do {
										System.out.println(String.format("%27s", "==Updating Contacts=="));
										
										if (updating_array_value == 0) {
											System.out.println("=There are no current contacts!=");
											break;
										} else {
											for (int i = 0; i < updating_array_value; i++){
													System.out.println(String.format("%16s", "["+ (i + 1) + "] Contact: " + name[i]));
												}
												// Prompt user to select contact to update
												System.out.println(String.format("%23s", "<- [" + (updating_array_value + 1) + "] Return"));
												System.out.print("which contact do you wish to update?: ");
												update = us_input.nextInt();
												
												// Allow user to update chosen contact
												if (update < (updating_array_value + 1) && update != 0){
													System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
													System.out.println(String.format("%27s", "=Upadting Contact [" + (update) + "]="));
													System.out.println("[1] Name: "+ name[update - 1]);
													System.out.println("[2] Contact Number: "+ contact_num[update - 1]);
													System.out.println("[3] Email Address: "+ em_address[update - 1]);
													System.out.println(String.format("%34s", "[4] Return to Updatable Contacts"));
													System.out.print("Choose which part you wish to update:");
													update_choice = us_input.nextInt();
													
													// Switch to update the name, contact number, or email address
													switch (update_choice){
														case 1:	// Update name
															System.out.println(String.format("%30s", "============================"));
															System.out.println("==Updating Name of Contact [" + update + "]==");
															System.out.print(String.format("%22s", "Updated Name: "));
															name_update = us_input.next();
															name[update - 1] = name_update;
															System.out.println("Name of contact [" + update + "] has successfuly changed to '" + name_update + "'=");				
															System.out.println(String.format("%30s", "============================"));
															break;
												
														case 2:	// Update contact number
															System.out.println(String.format("%30s", "============================"));
															System.out.println("==Updating Contact Number of Contact [" + update + "]==");
															System.out.print(String.format("%22s", "Updated Contact Number: "));
															contact_num_update = us_input.next();
															contact_num[update - 1] = contact_num_update;
															System.out.println("=Contact Number of contact [" + update + "] has successfuly changed to '" + contact_num_update + "'=");
															System.out.println(String.format("%30s", "============================"));
															break;
														
														case 3:	// Update email address
															System.out.println(String.format("%30s", "============================"));
															System.out.println("==Updating Email Address of Contact [" + update + "]==");
															System.out.print(String.format("%22s", "Updated Email Address: "));
															em_address_update = us_input.next();
															em_address[update - 1] = em_address_update;
															System.out.println("Email Address of contact [" + update + "] has successfuly changed to '" + em_address_update + "'=");	
															System.out.println(String.format("%30s", "============================"));
															break;
													
														case 4: // Return to update section
															System.out.println(String.format("%30s", "============================"));
															System.out.println("=Returning to set of Updatable Contacts=");
															System.out.println(String.format("%30s", "============================"));
															break;
														
														default: //	Re-runs the choices if condition is not met
															System.out.println(String.format("%30s", "============================"));
															System.out.println("The contact of your choice is unknown. Please choose what is provided");
															System.out.println(String.format("%30s", "============================"));
															valid_action = false;
															break;
													}
												} else if (update == (updating_array_value + 1)){ // Prompt to return to contacts
													System.out.println(String.format("%28s", "=Returning to Contacts="));
													break;
												} else {	// Re-runs the choices if condition is not met
													System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
													System.out.println("The contact of your choice is unknown, please choose what is provided.");
													System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
													valid_action = false;
												}
											}
										} while (!valid_action);
	                                break;
	                            case "4": // Delete a specific contact
	                                valid_action = false;
									do {
										System.out.println(String.format("%27s", "==Deleting Contacts=="));
										
										if (updating_array_value == 0) {
											System.out.println("=There are no current contacts!=");
											break;
										} else {
											for (int i = 0; i < updating_array_value; i++){
												System.out.println(String.format("%16s", "["+ (i + 1) + "] Contact: " + name[i]));
											}
											
											// Prompt user for contact to delete
											System.out.println(String.format("%23s", "<- [" + (updating_array_value + 1) + "] Return"));
											System.out.print("which contact do you wish to delete?: ");
											delete = us_input.nextInt();
											
											// Create updated arrays to hold contacts after deletion
											if (delete <= updating_array_value && delete != 0){
												if (updating_array_value >= name.length) {
													String[] updated_name = new String[updating_array_value - 1];
													String[] updated_contact_num = new String[updating_array_value - 1];
													String[] updated_em_address = new String[updating_array_value - 1];
	
													for (int i = 0, j = 0; i < updating_array_value; i++) {
														if (i != (delete - 1)){
															updated_name[j] = name[i];
															updated_contact_num[j] = contact_num[i];
															updated_em_address[j] = em_address[i];
															j++;
														}
													}
													
													// Update the original arrays to reflect the changes
													name = updated_name;
													contact_num = updated_contact_num;
													em_address = updated_em_address;
												}
												
												updating_array_value--;
												System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
												System.out.println(String.format("%30s", "============================"));
												System.out.println("=Contact [" + delete + "] Deleted Successfully=");
												System.out.println(String.format("%30s", "============================"));
												System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
												break;
												
											} else if (delete == (updating_array_value + 1)) {
												System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
												System.out.println(String.format("%30s", "============================"));
												System.out.println(String.format("%28s", "=Returning to Contacts="));
												System.out.println(String.format("%30s", "============================"));
												System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
												break;
											} else {
												System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
												System.out.println("The contact of your choice is unknown, please choose what is provided.");
												System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
												valid_action = false;
											}
										}
									} while (!valid_action);
	                                break;
	                            case "5": //Insert a specific contact
	                                valid_action = false;
	                                System.out.println(String.format("%29s", "==Inputting A New Contact=="));
	
									// Create new arrays to accommodate an additional contact
	                                if (updating_array_value >= name.length) {
	                                    String[] updated_name = new String[updating_array_value + 1];
	                                    String[] updated_contact_num = new String[updating_array_value + 1];
	                                    String[] updated_em_address = new String[updating_array_value + 1];
	
	                                    for (int i = 0; i < updating_array_value; i++) {
	                                        updated_name[i] = name[i];
	                                        updated_contact_num[i] = contact_num[i];
	                                        updated_em_address[i] = em_address[i];
	                                    }
										
										// Update the references to the new arrays
	                                    name = updated_name;
	                                    contact_num = updated_contact_num;
	                                    em_address = updated_em_address;
	                                }
									
									// Prompt user for the contact's name
	                                System.out.print(String.format("%7s","Name: "));
	                                name[updating_array_value] = us_input.next();
	                                
									// Prompt user for the contact's phone number
	                                System.out.print(String.format("%17s", "Contact Number: "));
	                                contact_num[updating_array_value] = us_input.next();
	                                
									// Prompt user for the contact's email address
	                                System.out.print(String.format("%16s","Email Address: "));
	                                em_address[updating_array_value] = us_input.next();
	                                
									System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
									System.out.println(String.format("%30s", "============================"));
									System.out.println(String.format("%31s", "=Contact Successfully Added!="));
									System.out.println(String.format("%30s", "============================"));
									System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
	                                updating_array_value++;
	                                break;
	                            case "6": // Case for exiting the program
									System.out.println(String.format("%30s", "================================"));
	                                System.out.println(String.format("%24s", "Exiting program!"));
									System.out.println(String.format("%30s", "================================"));
									valid_action = true; // Set valid action to true to break the loop
	                                valid_choice = true; // Indicate that a valid choice was made
	                                break;
	                            default: // Default case for invalid choices
									System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
	                                System.out.println(String.format("%28s", "Invalid choice, please enter a digit between the range (1-6)"));
									System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
									valid_action = false; // Set valid action to false to continue the loop
	                                break;
	                        }
	                    } while (!valid_action); // Loop until a valid action is performed
	                    break;
	                case "no": // Case for when the user chooses to exit
	                    valid_choice = true;
						System.out.println(String.format("%30s", "================================"));
	                    System.out.println(String.format("%15s", "Goodbye!"));
	                    System.out.println(String.format("%21s", "===Program Ended==="));
	                    break;
	                default: // Default case for invalid user input
						System.out.println(String.format("%30s", "≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡≡"));
	                    System.out.println("Invalid choice, please enter Yes or No only.");
	                    break;
	            }
	        } while (!valid_choice); // Continue looping until a valid choice is made
	        us_input.close();
	    }
	}
