// the applicant gets their money = 35% of cost per application.
// The organizer will also get 35% to their wallet, 
// Platform earns 30%. 

pragma solidity 0.9.0;

contract RevenueSharing {

using SafeMath for uint256;

struct Revenue{
    address revenueAddress;
    int balance;
}

struct applicant {
    address applicantAddress;
    uint32 applicantShare;
}

struct jobEvent {
    address eventAddress;
    uint32 eventID;
    uint32 eventShare;
}

struct recorem {
    address recoremAddress;
    uint32 recoremShare;
}

event webEvent_start
event webEvent_end

function getRevenue(companyAddress, eventID) return uint {
    require(companyAddress = msg.sender)

}

function applicantRevenue(uint _totalRevenue) payable {
    require (totalRevenue != 0)
    _totalRevenue = totalRevenue;
    applicantShare = 35 * _totalRevenue / 100;

}

function eventRevenue(uint _totalRevenue) payable {
    require (totalRevenue != 0)
    _totalRevenue = totalRevenue;
    eventShare = 35 * _totalRevenue / 100;
}

function recoremShare(uint _totalRevenue)payable {
    require (totalRevenue != 0)
    _totalRevenue = totalRevenue;
    recoremShare = 35 * _totalRevenue / 100;
}


}
